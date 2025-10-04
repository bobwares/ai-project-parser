# Infrastructure-as-Code (IaC) Report



## File: ./iac/apigateway.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source apigateway.tf
 * @author Bobwares
 * @version 2.1.0
 * @description HTTP API, CloudWatch access logging, integrations, routes,
 *              and invoke permissions for CRUD operations.  Paths are derived
 *              from local.domain_resource (schema/domain.json).
 * @updated 2025-06-26T13:05:00-05:00
 */

/*-----------------------------------------------------------------------------
# aws_cloudwatch_log_group.api_access
# ---------------------------------------------------------------------------
# Access-log destination for the HTTP API stage.  Logs are retained 14 days
# and charged only for storage/ingest (~MB per month in dev).  A single log
# group per environment keeps queries simple: /aws/apigw/<api_name>.
-----------------------------------------------------------------------------*/
resource "aws_cloudwatch_log_group" "api_access" {
  name              = "/aws/apigw/${local.api_name}"
  retention_in_days = 1
}

/*-----------------------------------------------------------------------------
# aws_apigatewayv2_stage.default
# ---------------------------------------------------------------------------
# Default stage for the HTTP API.  `auto_deploy = true` publishes each new
# route immediately after `terraform apply`.  Access logs are streamed to the
# CloudWatch group above in structured JSON, keyed by requestId.
-----------------------------------------------------------------------------*/
resource "aws_apigatewayv2_stage" "default" {
  api_id      = aws_apigatewayv2_api.http.id
  name        = var.environment                      # e.g. dev, stage, prod
  auto_deploy = true

  access_log_settings {
    destination_arn = aws_cloudwatch_log_group.api_access.arn
    format = jsonencode({
      requestId = "$context.requestId",
      routeKey  = "$context.routeKey",
      status    = "$context.status",
      latency   = "$context.responseLatency",
      error     = "$context.error.message"
    })
  }
}

/*-----------------------------------------------------------------------------
# aws_apigatewayv2_api.http
# ---------------------------------------------------------------------------
# Single regional HTTP API (API Gateway v2).  The name combines the domain
# title and environment for readability, e.g. customerprofile-api-dev.
-----------------------------------------------------------------------------*/
resource "aws_apigatewayv2_api" "http" {
  name          = local.api_name
  protocol_type = "HTTP"            # Lower cost & latency than REST v1
}

/*-----------------------------------------------------------------------------
# aws_apigatewayv2_integration.verb
# ---------------------------------------------------------------------------
# One AWS_PROXY integration per Lambda handler (create, list, get, update,
# patch, delete).  Using `for_each` keeps the map in sync with module.lambda.
-----------------------------------------------------------------------------*/
resource "aws_apigatewayv2_integration" "verb" {
  for_each               = module.lambda
  api_id                 = aws_apigatewayv2_api.http.id
  integration_type       = "AWS_PROXY"                 # Full pass-through
  integration_uri        = each.value.lambda_function_invoke_arn
  payload_format_version = "2.0"
}

/*-----------------------------------------------------------------------------
# ROUTES ─────────────────────────────────────────────────────────────────────
# Six routes provide standard CRUD semantics.  `${local.domain_resource}`
# comes from schema/domain.json → "resource".
-----------------------------------------------------------------------------*/

# POST /<resource>          → Create entity
resource "aws_apigatewayv2_route" "create" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "POST /${local.domain_resource}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["create"].id}"
}

# GET  /<resource>          → List entities
resource "aws_apigatewayv2_route" "list" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "GET /${local.domain_resource}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["list"].id}"
}

# GET  /<resource>/{id}     → Fetch one entity
resource "aws_apigatewayv2_route" "get" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "GET /${local.domain_resource}/{id}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["get"].id}"
}

# PUT  /<resource>/{id}     → Full update
resource "aws_apigatewayv2_route" "update" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "PUT /${local.domain_resource}/{id}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["update"].id}"
}

# PATCH /<resource>/{id}    → Partial update
resource "aws_apigatewayv2_route" "patch" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "PATCH /${local.domain_resource}/{id}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["patch"].id}"
}

# DELETE /<resource>/{id}   → Remove entity
resource "aws_apigatewayv2_route" "delete" {
  api_id    = aws_apigatewayv2_api.http.id
  route_key = "DELETE /${local.domain_resource}/{id}"
  target    = "integrations/${aws_apigatewayv2_integration.verb["delete"].id}"
}

/*-----------------------------------------------------------------------------
# aws_lambda_permission.allow_apigw
# ---------------------------------------------------------------------------
# Grants API Gateway permission to invoke each Lambda handler.  Source ARN is
# scoped to this API and stage for least privilege.
-----------------------------------------------------------------------------*/
resource "aws_lambda_permission" "allow_apigw" {
  for_each      = module.lambda
  statement_id  = "AllowInvoke-${each.key}"
  action        = "lambda:InvokeFunction"
  function_name = each.value.lambda_function_name
  principal     = "apigateway.amazonaws.com"
  source_arn    = "${aws_apigatewayv2_api.http.execution_arn}/${var.environment}/*"
}
```

## File: ./iac/dynamodb.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source dynamodb.tf
 * @author Bobwares
 * @version 2.0.1
 * @description DynamoDB single-table with GSI.
 * @updated 2025-06-25T14:00:08Z
*/

resource "aws_dynamodb_table" "single" {
  name         = "${local.domain_title}-${var.environment}"
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "pk"
  range_key    = "sk"

  attribute {
    name = "pk"
    type = "S"
  }

  attribute {
    name = "sk"
    type = "S"
  }

  attribute {
    name = "gsi1pk"
    type = "S"
  }

  global_secondary_index {
    name            = "gsi1"
    hash_key        = "gsi1pk"
    range_key       = "sk"
    projection_type = "ALL"
  }

  tags = merge(var.tags, {
    Domain      = local.domain_title
    Environment = var.environment
  })
}
```

## File: ./iac/iam.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source iam.tf
 * @author Bobwares
 * @version 2.1.0
 * @description Inline IAM policies used by the Lambda CRUD functions.  Each
 *              policy grants the minimum set of DynamoDB actions required by
 *              its verb.  Policies are injected directly into the Lambda
 *              module via `policy_json`, avoiding separate IAM resources.
 * @updated 2025-06-26T12:47:00-05:00
 */

/*-----------------------------------------------------------------------------
# data.aws_iam_policy_document.ddb_read
# ---------------------------------------------------------------------------
# Read-only access:
#   - GetItem   → fetch one item by PK/SK
#   - Query     → list items via PK and/or GSI
# Includes indexes so queries on gsi1 work.  Used by `list` and `get`
# Lambda handlers.
-----------------------------------------------------------------------------*/
data "aws_iam_policy_document" "ddb_read" {
  statement {
    actions = [
      "dynamodb:GetItem",
      "dynamodb:Query"
    ]
    resources = [
      aws_dynamodb_table.single.arn,
      "${aws_dynamodb_table.single.arn}/index/*"   # gsi1
    ]
  }
}

/*-----------------------------------------------------------------------------
# data.aws_iam_policy_document.ddb_write
# ---------------------------------------------------------------------------
# Write access without deletes:
#   - PutItem      → create new entity
#   - UpdateItem   → full/partial overwrite
# Targets the base table only (no indexes).  Used by `create`, `update`,
# and `patch` handlers.
-----------------------------------------------------------------------------*/
data "aws_iam_policy_document" "ddb_write" {
  statement {
    actions = [
      "dynamodb:PutItem",
      "dynamodb:UpdateItem"
    ]
    resources = [
      aws_dynamodb_table.single.arn
    ]
  }
}

/*-----------------------------------------------------------------------------
# data.aws_iam_policy_document.ddb_delete
# ---------------------------------------------------------------------------
# Delete access:
#   - DeleteItem   → remove entity
# Limited to the base table.  Used exclusively by the `delete` handler.
-----------------------------------------------------------------------------*/
data "aws_iam_policy_document" "ddb_delete" {
  statement {
    actions = [
      "dynamodb:DeleteItem"
    ]
    resources = [
      aws_dynamodb_table.single.arn
    ]
  }
}
```

## File: ./iac/lambda.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source lambda.tf
 * @author Bobwares
 * @version 2.1.0
 * @description Lambda functions for CRUD verbs.  Each entry is packaged
 *              separately, receives verb-specific IAM, and now has pinned
 *              memory_size/timeout for predictable performance.
 * @updated 2025-06-26T12:45:00-05:00
 */

/*-----------------------------------------------------------------------------
# locals.lambda_map
# ---------------------------------------------------------------------------
# Central verb-to-configuration map.  Adding a new verb (e.g., bulkUpdate)
# requires only a new element here; the module block below will pick it up.
# Keys:
#   - handler      → file.function exported in the ZIP
#   - source_dir   → path to compiled bundle
#   - policy_json  → inline IAM policy (read/write/delete)
#   - memory       → MB
#   - timeout      → seconds
-----------------------------------------------------------------------------*/
locals {
lambda_map = {
create = {
handler     = "create.handler"
source_dir  = "${path.root}/../dist/handlers/create"
policy_json = data.aws_iam_policy_document.ddb_write.json
memory      = 256
timeout     = 10
}
list = {
handler     = "list.handler"
source_dir  = "${path.root}/../dist/handlers/list"
policy_json = data.aws_iam_policy_document.ddb_read.json
memory      = 128
timeout     = 5
}
get = {
handler     = "get.handler"
source_dir  = "${path.root}/../dist/handlers/get"
policy_json = data.aws_iam_policy_document.ddb_read.json
memory      = 128
timeout     = 5
}
update = {
handler     = "update.handler"
source_dir  = "${path.root}/../dist/handlers/update"
policy_json = data.aws_iam_policy_document.ddb_write.json
memory      = 256
timeout     = 10
}
patch = {
handler     = "patch.handler"
source_dir  = "${path.root}/../dist/handlers/patch"
policy_json = data.aws_iam_policy_document.ddb_write.json
memory      = 256
timeout     = 10
}
delete = {
handler     = "delete.handler"
source_dir  = "${path.root}/../dist/handlers/delete"
policy_json = data.aws_iam_policy_document.ddb_delete.json
memory      = 128
timeout     = 5
}
}
}

/*-----------------------------------------------------------------------------
# module.lambda
# ---------------------------------------------------------------------------
# One Lambda per CRUD verb via terraform-aws-modules/lambda.  Memory and
# timeout are pulled from local.lambda_map.  IAM is verb-scoped (least
# privilege).  Tags include the verb for easy CloudWatch filtering.
-----------------------------------------------------------------------------*/
module "lambda" {
source  = "terraform-aws-modules/lambda/aws"
version = "7.21.0"

for_each = local.lambda_map

function_name = "${local.domain_title}-${each.key}-${var.environment}"
runtime       = var.lambda_runtime
handler       = each.value.handler
source_path   = each.value.source_dir

# Performance limits
memory_size   = each.value.memory
timeout       = each.value.timeout

# IAM
attach_policy_json = true
policy_json        = each.value.policy_json

# Environment
environment_variables = {
TABLE_NAME                          = aws_dynamodb_table.single.name
DOMAIN_SCHEMA                       = jsonencode(local.domain_schema)
AWS_NODEJS_CONNECTION_REUSE_ENABLED = 1
POWERTOOLS_SERVICE_NAME             = local.domain_title
}

tags = merge(var.tags, { Verb = each.key })
}

```

## File: ./iac/local_file.tf

```hcl
resource "local_file" "api_url_test" {
  content  = aws_apigatewayv2_api.http.api_endpoint
  filename = "${path.root}/../test/http/api_url.txt"
}
```

## File: ./iac/locals.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source locals.tf
 * @author Bobwares
 * @version 2.1.0
 * @description Derive API names and helpers from schema_path (= envs/*.tfvars).
 * @updated 2025-06-25
 */

locals {
  # ---------------------------------------------------------------------------
  # domain_schema
  # ---------------------------------------------------------------------------
  # Reads and decodes the JSON schema specified by var.schema_path.
  # Example path comes from envs/dev.tfvars → `schema_path = "../schema/domain.json"`.
  # The schema must include at least a `"title"` field; `"resource"` is optional
  # but recommended for API path generation.
  domain_schema = jsondecode(file(var.schema_path))

  # ---------------------------------------------------------------------------
  # domain_title
  # ---------------------------------------------------------------------------
  # Lower-cased version of schema["title"] (e.g., "CustomerProfile" → "customerprofile").
  # Used as a base for naming AWS resources in a consistent, environment-agnostic way.
  domain_title  = lower(local.domain_schema.title)

  # ---------------------------------------------------------------------------
  # domain_resource
  # ---------------------------------------------------------------------------
  # REST path segment used by API Gateway routes.
  # If the `"resource"` key is missing in the schema, we fall back to `"items"`
  # so Terraform plans remain valid (CI won’t fail on missing keys).
  domain_resource = lookup(local.domain_schema, "resource", "items")

  # ---------------------------------------------------------------------------
  # api_name
  # ---------------------------------------------------------------------------
  # Combines domain_title with the current environment to produce a unique,
  # readable API Gateway name. Example: "customerprofile-api-dev".
  api_name = "${local.domain_title}-api-${var.environment}"
}
```

## File: ./iac/provider.tf

```hcl
/**
 * @application Infrastructure-as-Code (IaC)
 * @source provider.tf
 * @author Codex
 * @version 2.1.0
 * @description Terraform provider configuration with remote state placeholders.
 * @updated 2025-06-25T14:00:08Z
*/

terraform {
  required_version = ">= 1.8.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
    local = {
      source  = "hashicorp/local"
      version = "~> 2.0"
    }
  }

  backend "local" {
    path = "terraform.tfstate"
    # To use remote state, configure:
    # bucket         = "<state-bucket>"
    # key            = "customer-api/terraform.tfstate"
    # region         = var.aws_region
    # dynamodb_table = "<lock-table>"
  }
}

provider "aws" {
  region = var.aws_region
}
```

