# Configuration Files Compilation

## JavaScript / TypeScript

### File: ./iac/.terraform/modules/lambda/tests/fixtures/node-app/package.json

```json
{
  "name": "app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
  },
  "devDependencies": {
    "axios": "^1.7.3"
  }
}

```

### File: ./tsconfig.json

```json
{
  "compilerOptions": {
    /* Language and Module Resolution */
    "target": "ES2022",
    "module": "es2022",
    "moduleResolution": "nodenext",
    "rootDir": "src",
    "outDir": "dist",
    "resolveJsonModule": true,
    "allowSyntheticDefaultImports": true,

    /* Strictness Options */
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noImplicitOverride": true,
    "exactOptionalPropertyTypes": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "noImplicitReturns": true,

    /* Decorators & Metadata (for NestJS/Angular/etc.) */
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,

    /* Performance */
    "skipLibCheck": true,
    "incremental": true,
    "tsBuildInfoFile": ".tsbuildinfo",

    /* Source Maps */
    "sourceMap": true
  },
  "include": ["src/**/*", "test/**/*"],
  "exclude": ["node_modules", "dist"]
}

```

## Python

### File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app-src-poetry/pyproject.toml

```toml
[tool.poetry]
name = "python-app-src-poetry"
version = "0.1.0"
description = ""
authors = ["Your Name <you@example.com>"]
readme = "README.md"
packages = [{include = "python_app_src_poetry", from = "src"}]

[tool.poetry.dependencies]
python = "^3.9"
colorful = "^0.5.5"


[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"

```

### File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app1/requirements.txt

```bash
colorful

```

### File: ./iac/.terraform/modules/lambda/tox.ini

```ini
[tox]
skipsdist=True

[testenv]
deps =
  pytest==7.1.3
commands =
  python -m pytest {posargs} tests/

```

## Java

### File: ./iac/.terraform/modules/lambda/examples/fixtures/runtimes/java21/build.gradle

```groovy
plugins {
    id 'java'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'com.amazonaws:aws-lambda-java-core:1.2.1'
    implementation 'org.slf4j:slf4j-nop:2.0.6'
    implementation 'com.fasterxml.jackson.core:jackson-databind:2.17.0'
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.2'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.2'
}

test {
    useJUnitPlatform()
}

// Using terraform-aws-lambda module, there is no need to make Zip archive by Gradle. Terraform AWS module will make it for you.
// task buildZip(type: Zip) {
//     from compileJava
//     from processResources
//     into('lib') {
//         from configurations.runtimeClasspath
//     }
// }

task copyFiles(type: Copy) {
    into("$buildDir/output")

    from sourceSets.main.output

    into('lib') {
        from configurations.runtimeClasspath
    }
}

build.dependsOn copyFiles

```

## DevOps / Infrastructure

### File: ./iac/.terraform/modules/lambda/examples/container-image/context/Dockerfile

```docker
# `--platform` argument is used to be able to build docker images when using another platform (e.g. Apple M1)
FROM --platform=linux/x86_64 scratch AS first_stage

ARG FOO

ENV FOO $FOO

COPY empty /empty

FROM first_stage AS second_stage

COPY empty /empty_two

```

## Miscellaneous

### File: ./iac/.terraform/modules/lambda/.gitignore

```bash
# Local .terraform directories
**/.terraform/*

# Terraform lockfile
.terraform.lock.hcl

# .tfstate files
*.tfstate
*.tfstate.*
*.tfplan

# Crash log files
crash.log

# Exclude all .tfvars files, which are likely to contain sentitive data, such as
# password, private keys, and other secrets. These should not be part of version
# control as they are data points which are potentially sensitive and subject
# to change depending on the environment.
*.tfvars

# Ignore override files as they are usually used to override resources locally and so
# are not checked in
override.tf
override.tf.json
*_override.tf
*_override.tf.json

# Ignore CLI configuration files
.terraformrc
terraform.rc

# Lambda directories
builds/
__pycache__/

# Test directories
.tox

```

