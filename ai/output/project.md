## AI Prompt Context Instructions
    - This file includes the current of the application.
    - Always include metadata header section for project at the top of each source code file.
    - Definition of Metadata header section:

```markdown
# LangChain PoC - Minimal Chat Example
# Package: {{package}}
# File: {{file name}}
# Version: 2.0.29
# Author: Bobwares
# Date: {{current date/ time}}
# Description: document the function of the code.
#

```

- Update version each time new code is generated.   
- create file version.md with updated version number and list of changes.
- follow code formatting standards:   PEP 8: E303 too many blank lines (2)
## About This Project

## Project Overview
* 
* **Name**: `LangChain ReAct Agent Implementation`
* **Version**: `1.0.0`
* **Description**: Iterates over configured ReAct tasks, running each through
*  a general-purpose ReAct pipeline, printing results, and saving each
*  run’s outputs under history/{YYYYMMDD_HHMMSS}/ at the project root.
* **Author**: Bobwares ([bobwares@outlook.com](mailto:bobwares@outlook.com))



# Version History

## 1.0.0
- Initial proof-of-concept release.

## Technology Stack


### Application Layer

#### Language

* **Python** `^3.12`

    * Modern version with improved performance, type hinting, and async support.

---

### Core Dependencies

| Package               | Version  | Purpose                                                    |
| --------------------- | -------- | ---------------------------------------------------------- |
| `langchain`           | `~0.3.0` | Core library for building LLM-driven applications          |
| `langchain-openai`    | `~0.3.0` | OpenAI model bindings for LangChain                        |
| `python-dotenv`       | `^1.0`   | Loads environment variables from `.env` files              |


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


# Source Code

## File: ./eslint.config.js
```javascript
// App: Full-Stack Application
// Directory: api
// File: eslint.config.js
// Version: 1.0.0
// Author: Bobwares CodeBot
// Date: 2025-06-12T06:58:30Z
// Description: Configure ESLint using the flat config format.

import typescriptParser from '@typescript-eslint/parser';
import typescriptPlugin from '@typescript-eslint/eslint-plugin';
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import { dirname } from 'path';
import { fileURLToPath } from 'url';

const __dirname = dirname(fileURLToPath(import.meta.url));

export default [
  {
    ignores: ['dist/**', 'node_modules/**', 'test/**'],
  },
  eslintConfigPrettier,
  {
    files: ['**/*.ts', '**/*.tsx'],
    languageOptions: {
      parser: typescriptParser,
      parserOptions: {
        project: ['./tsconfig.json'],
        tsconfigRootDir: __dirname,
        sourceType: 'module',
      },
    },
    plugins: {
      '@typescript-eslint': typescriptPlugin,
      prettier: prettierPlugin,
    },
    rules: {
      'prettier/prettier': 'error',
      'no-console': 'warn',
      'no-debugger': 'error',
      'no-unused-vars': 'warn',
      'no-implicit-coercion': 'error',
      eqeqeq: ['error', 'always'],
      '@typescript-eslint/no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
      'arrow-body-style': 'off',
      'prefer-arrow-callback': 'off',
    },
  },
];
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/nodejs14.x-app1/index.js
```javascript
'use strict';

module.exports.hello = async (event) => {
  console.log(event);
  return {
    statusCode: 200,
    body: JSON.stringify(
      {
        message: `Go Serverless.tf! Your Nodejs function executed successfully!`,
        input: event,
      },
      null,
      2
    ),
  };
};
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app-poetry/index.py
```python
def lambda_handler(event, context):
    print("Hello from app1!")

    return event
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app-src-poetry/src/python_app_src_poetry/__init__.py
```python
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app-src-poetry/tests/__init__.py
```python
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app1/index.py
```python
def lambda_handler(event, context):
    print("Hello from app1!")

    return event
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/python-app2/index.py
```python
import logging
import boto3
import os
from uuid import uuid4

# See https://docs.aws.amazon.com/lambda/latest/dg/python-logging.html
logger = logging.getLogger()
logger.setLevel(logging.INFO)

logging.getLogger("boto3").setLevel(logging.DEBUG)
logging.getLogger("botocore").setLevel(logging.DEBUG)

bucketName = os.environ["BUCKET_NAME"]
regionName = os.environ["REGION_NAME"]


def lambda_handler(event, context):
    client = boto3.client("s3", regionName)
    response = client.put_object(
        Bucket=bucketName, Key=str(uuid4()), Body=bytearray("Hello, World!", "utf-8")
    )

    logger.info(response)

    return response
```

## File: ./iac/.terraform/modules/lambda/examples/fixtures/runtimes/java21/src/main/java/example/Handler.java
```java
package example;

import com.amazonaws.services.lambda.runtime.Context;
import com.amazonaws.services.lambda.runtime.LambdaLogger;
import com.amazonaws.services.lambda.runtime.RequestHandler;

import java.util.Map;

// Handler value: example.Handler
public class Handler implements RequestHandler<Map<String,String>, String>{

  @Override
  public String handleRequest(Map<String,String> event, Context context)
  {
    LambdaLogger logger = context.getLogger();
    logger.log("EVENT TYPE: " + event.getClass());
    return "Hello from serverless.tf!!!";
  }
}
```

## File: ./iac/.terraform/modules/lambda/package.py
```python
# coding: utf-8

import sys

if sys.version_info < (3, 6):
    raise RuntimeError("A python version 3.6 or newer is required")

import os
import re
import time
import stat
import json
import shlex
import shutil
import hashlib
import zipfile
import argparse
import datetime
import tempfile
import operator
import platform
import subprocess
from subprocess import check_call, check_output
from contextlib import contextmanager
from base64 import b64encode
import logging

PY38 = sys.version_info >= (3, 8)
PY37 = sys.version_info >= (3, 7)
PY36 = sys.version_info >= (3, 6)

WINDOWS = platform.system() == "Windows"
OSX = platform.system() == "Darwin"

################################################################################
# Logging

DEBUG2 = 9
DEBUG3 = 8
DUMP_ENV = 1

log_handler = None
log = logging.getLogger()
cmd_log = logging.getLogger("cmd")


def configure_logging(use_tf_stderr=False):
    global log_handler

    logging.addLevelName(DEBUG2, "DEBUG2")
    logging.addLevelName(DEBUG3, "DEBUG3")
    logging.addLevelName(DUMP_ENV, "DUMP_ENV")

    class LogFormatter(logging.Formatter):
        default_format = "%(message)s"
        formats = {
            "root": default_format,
            "build": default_format,
            "prepare": "[{}] %(name)s: %(message)s".format(os.getpid()),
            "cmd": "> %(message)s",
            "": "%(name)s: %(message)s",
        }

        def formatMessage(self, record):
            prefix = record.name.rsplit(".")
            self._style._fmt = self.formats.get(prefix[0], self.formats[""])
            return super().formatMessage(record)

    tf_stderr_fd = 5
    log_stream = sys.stderr
    if use_tf_stderr:
        try:
            if os.isatty(tf_stderr_fd):
                log_stream = os.fdopen(tf_stderr_fd, mode="w")
        except OSError:
            pass

    log_handler = logging.StreamHandler(stream=log_stream)
    log_handler.setFormatter(LogFormatter())

    log.addHandler(log_handler)
    log.setLevel(logging.INFO)


def dump_env():
    if log.isEnabledFor(DUMP_ENV):
        log.debug("ENV: %s", json.dumps(dict(os.environ), indent=2))


################################################################################
# Backports


def shlex_join(split_command):
    """Return a shell-escaped string from *split_command*."""
    return " ".join(shlex.quote(arg) for arg in split_command)


################################################################################
# Common functions


def abort(message):
    """Exits with an error message."""
    log.error(message)
    sys.exit(1)


@contextmanager
def cd(path, silent=False):
    """Changes the working directory."""
    cwd = os.getcwd()
    if not silent:
        cmd_log.info("cd %s", shlex.quote(path))
    try:
        os.chdir(path)
        yield
    finally:
        os.chdir(cwd)


@contextmanager
def tempdir(dir=None):
    """Creates a temporary directory and then deletes it afterwards."""
    prefix = "terraform-aws-lambda-"
    path = tempfile.mkdtemp(prefix=prefix, dir=dir)
    abs_path = os.path.abspath(path)
    cmd_log.info("mktemp -d %sXXXXXXXX # %s", prefix, shlex.quote(abs_path))
    try:
        yield abs_path
    finally:
        shutil.rmtree(abs_path)


def list_files(top_path, log=None):
    """
    Returns a sorted list of all files in a directory.
    """

    if log:
        log = log.getChild("ls")

    results = []

    for root, dirs, files in os.walk(top_path, followlinks=True):
        # Sort directories and files to ensure they are always processed in the same order
        dirs.sort()
        files.sort()
        for file_name in files:
            file_path = os.path.join(root, file_name)
            relative_path = os.path.relpath(file_path, top_path)
            results.append(relative_path)
            if log:
                log.debug(relative_path)

    results.sort()
    return results


def dataclass(name):
    typ = type(
        name,
        (dict,),
        {
            "__getattr__": lambda self, x: self.get(x),
            "__init__": lambda self, **k: self.update(k),
        },
    )
    return typ


def datatree(name, **fields):
    def decode_json(k, v):
        if v and isinstance(v, str) and v[0] in '"[{':
            try:
                o = json.loads(v)
                if isinstance(o, dict):
                    return dataclass(k)(**o)
                return o
            except json.JSONDecodeError:
                pass
        return v

    return dataclass(name)(
        **dict(
            (
                (k, datatree(k, **v) if isinstance(v, dict) else decode_json(k, v))
                for k, v in fields.items()
            )
        )
    )


def timestamp_now_ns():
    timestamp = datetime.datetime.now().timestamp()
    timestamp = int(timestamp * 10**7) * 10**2
    return timestamp


def source_code_hash(bytes):
    return b64encode(hashlib.sha256(bytes).digest()).decode()


def yesno_bool(val):
    if val is None:
        return
    if isinstance(val, bool):
        return val
    if isinstance(val, int):
        return bool(val)
    if isinstance(val, str):
        if val.isnumeric():
            return bool(int(val))
        val = val.lower()
        if val in ("true", "yes", "y"):
            return True
        elif val in ("false", "no", "n"):
            return False
        else:
            raise ValueError("Unsupported value: %s" % val)
    return False


################################################################################
# Packaging functions


def emit_dir_content(base_dir):
    for root, dirs, files in os.walk(base_dir, followlinks=True):
        # Sort directories and files to ensure they are always processed in the same order
        dirs.sort()
        files.sort()
        if root != base_dir:
            yield os.path.normpath(root)
        for name in files:
            yield os.path.normpath(os.path.join(root, name))


def generate_content_hash(source_paths, hash_func=hashlib.sha256, log=None):
    """
    Generate a content hash of the source paths.
    """

    if log:
        log = log.getChild("hash")

    hash_obj = hash_func()

    for source_path in source_paths:
        if os.path.isdir(source_path):
            source_dir = source_path
            _log = log if log.isEnabledFor(DEBUG3) else None
            for source_file in list_files(source_dir, log=_log):
                update_hash(hash_obj, source_dir, source_file)
                if log:
                    log.debug(os.path.join(source_dir, source_file))
        else:
            source_dir = os.path.dirname(source_path)
            source_file = os.path.relpath(source_path, source_dir)
            update_hash(hash_obj, source_dir, source_file)
            if log:
                log.debug(source_path)

    return hash_obj


def update_hash(hash_obj, file_root, file_path):
    """
    Update a hashlib object with the relative path and contents of a file.
    """

    relative_path = os.path.join(file_root, file_path)
    hash_obj.update(relative_path.encode())

    try:
        with open(relative_path, "rb") as open_file:
            while True:
                data = open_file.read(1024 * 8)
                if not data:
                    break
                hash_obj.update(data)
    # ignore broken symlinks content to don't fail on `terraform destroy` command
    except FileNotFoundError:
        pass


class ZipWriteStream:
    """"""

    def __init__(
        self,
        zip_filename,
        compress_type=zipfile.ZIP_DEFLATED,
        compresslevel=None,
        timestamp=None,
    ):
        self.timestamp = timestamp
        self.filename = zip_filename

        if not (self.filename and isinstance(self.filename, str)):
            raise ValueError("Zip file path must be provided")

        self._tmp_filename = None
        self._compress_type = compress_type
        self._compresslevel = compresslevel
        self._zip = None

        self._log = logging.getLogger("zip")

    def open(self):
        if self._tmp_filename:
            raise zipfile.BadZipFile("ZipStream object can't be reused")
        self._ensure_base_path(self.filename)
        self._tmp_filename = "{}.tmp".format(self.filename)
        self._log.info("creating '%s' archive", self.filename)
        self._zip = zipfile.ZipFile(self._tmp_filename, "w", self._compress_type)
        return self

    def close(self, failed=False):
        self._zip.close()
        self._zip = None
        if not os.path.exists(self._tmp_filename):
            return
        if failed:
            os.unlink(self._tmp_filename)
        else:
            os.replace(self._tmp_filename, self.filename)

    def __enter__(self):
        return self.open()

    def __exit__(self, exc_type, exc_val, exc_tb):
        if exc_type is not None:
            self._log.exception("Error during zip archive creation")
            self.close(failed=True)
            raise SystemExit(1)
        self.close()

    def _ensure_open(self):
        if self._zip is not None:
            return True
        if self._tmp_filename:
            raise zipfile.BadZipFile("ZipWriteStream object can't be reused")
        raise zipfile.BadZipFile("ZipWriteStream should be opened first")

    def _ensure_base_path(self, zip_filename):
        archive_dir = os.path.dirname(zip_filename)

        if archive_dir and not os.path.exists(archive_dir):
            self._log.info("creating %s", archive_dir)
            os.makedirs(archive_dir, exist_ok=True)

    def write_dirs(self, *base_dirs, prefix=None, timestamp=None):
        """
        Writes a directory content to a prefix inside of a zip archive
        """
        self._ensure_open()
        for base_dir in base_dirs:
            self._log.info("adding content of directory: %s", base_dir)
            for path in emit_dir_content(base_dir):
                arcname = os.path.relpath(path, base_dir)
                self._write_file(path, prefix, arcname, timestamp)

    def write_files(self, files_stream, prefix=None, timestamp=None):
        """
        Expects just files stream, directories will be created automatically
        """
        self._ensure_open()
        for file_path, arcname in files_stream:
            self._write_file(file_path, prefix, arcname, timestamp)

    def write_file(self, file_path, prefix=None, name=None, timestamp=None):
        """
        Reads a file and writes it to a prefix
        or a full qualified name in a zip archive
        """
        self._ensure_open()
        self._write_file(file_path, prefix, name, timestamp)

    def _write_file(self, file_path, prefix=None, name=None, timestamp=None):
        arcname = name if name else os.path.basename(file_path)
        if prefix:
            arcname = os.path.join(prefix, arcname)
        zinfo = self._make_zinfo_from_file(file_path, arcname)
        if zinfo.is_dir():
            self._log.info("adding: %s/", arcname)
        else:
            self._log.info("adding: %s", arcname)
        if timestamp is None:
            timestamp = self.timestamp
        date_time = self._timestamp_to_date_time(timestamp)
        if date_time:
            self._update_zinfo(zinfo, date_time=date_time)
        self._write_zinfo(zinfo, file_path)

    def write_file_obj(self, file_path, data, prefix=None, timestamp=None):
        """
        Write a data to a zip archive by a full qualified archive file path
        """
        self._ensure_open()
        raise NotImplementedError

    def _write_zinfo(self, zinfo, filename, compress_type=None, compresslevel=None):
        self._ensure_open()

        zip = self._zip

        if not zip.fp:
            raise ValueError("Attempt to write to ZIP archive that was already closed")
        if zip._writing:
            raise ValueError(
                "Can't write to ZIP archive while an open writing handle exists"
            )

        if zinfo.is_dir():
            zinfo.compress_size = 0
            zinfo.CRC = 0
        else:
            if compress_type is not None:
                zinfo.compress_type = compress_type
            else:
                zinfo.compress_type = self._compress_type

            if PY37:
                if compresslevel is not None:
                    zinfo._compresslevel = compresslevel
                else:
                    zinfo._compresslevel = self._compresslevel

        if zinfo.is_dir():
            with zip._lock:
                if zip._seekable:
                    zip.fp.seek(zip.start_dir)
                zinfo.header_offset = zip.fp.tell()  # Start of header bytes
                if zinfo.compress_type == zipfile.ZIP_LZMA:
                    # Compressed data includes an end-of-stream (EOS) marker
                    zinfo.flag_bits |= 0x02

                zip._writecheck(zinfo)
                zip._didModify = True

                zip.filelist.append(zinfo)
                zip.NameToInfo[zinfo.filename] = zinfo
                zip.fp.write(zinfo.FileHeader(False))
                zip.start_dir = zip.fp.tell()
        else:
            with open(filename, "rb") as src, zip.open(zinfo, "w") as dest:
                shutil.copyfileobj(src, dest, 1024 * 8)

    def _make_zinfo_from_file(self, filename, arcname=None):
        if PY38:
            zinfo_func = zipfile.ZipInfo.from_file
            strict_timestamps = self._zip._strict_timestamps
        else:
            zinfo_func = self._zinfo_from_file
            strict_timestamps = True

        return zinfo_func(filename, arcname, strict_timestamps=strict_timestamps)

    @staticmethod
    def _update_zinfo(zinfo, date_time):
        zinfo.date_time = date_time

    # Borrowed from python 3.8 zipfile.py library
    # due to the need of strict_timestamps functionality.
    @staticmethod
    def _zinfo_from_file(filename, arcname=None, *, strict_timestamps=True):
        """Construct an appropriate ZipInfo for a file on the filesystem.

        filename should be the path to a file or directory on the filesystem.

        arcname is the name which it will have within the archive (by default,
        this will be the same as filename, but without a drive letter and with
        leading path separators removed).
        """
        if isinstance(filename, os.PathLike):
            filename = os.fspath(filename)
        st = os.stat(filename)
        isdir = stat.S_ISDIR(st.st_mode)
        mtime = time.localtime(st.st_mtime)
        date_time = mtime[0:6]
        if strict_timestamps and date_time[0] < 1980:
            date_time = (1980, 1, 1, 0, 0, 0)
        elif strict_timestamps and date_time[0] > 2107:
            date_time = (2107, 12, 31, 23, 59, 59)
        # Create ZipInfo instance to store file information
        if arcname is None:
            arcname = filename
        arcname = os.path.normpath(os.path.splitdrive(arcname)[1])
        while arcname[0] in (os.sep, os.altsep):
            arcname = arcname[1:]
        if isdir:
            arcname += "/"
        zinfo = zipfile.ZipInfo(arcname, date_time)
        zinfo.external_attr = (st.st_mode & 0xFFFF) << 16  # Unix attributes
        if isdir:
            zinfo.file_size = 0
            zinfo.external_attr |= 0x10  # MS-DOS directory flag
        else:
            zinfo.file_size = st.st_size

        return zinfo

    @staticmethod
    def _timestamp_to_date_time(timestamp):
        def str_int_to_timestamp(s):
            min_zip_ts = datetime.datetime(1980, 1, 1).timestamp()
            ts = int(s)
            if ts < min_zip_ts:
                return min_zip_ts
            deg = len(str(int(s))) - 9
            if deg < 0:
                ts = ts * 10**deg
            return ts

        date_time = None
        if timestamp is not None:
            if isinstance(timestamp, str):
                if timestamp.isnumeric():
                    timestamp = str_int_to_timestamp(timestamp)
                else:
                    timestamp = float(timestamp)
            elif isinstance(timestamp, int):
                timestamp = str_int_to_timestamp(str(timestamp))

            date_time = datetime.datetime.fromtimestamp(timestamp).timetuple()
            date_time = date_time[:6]
            if date_time[0] < 1980:
                raise ValueError("ZIP does not support timestamps before 1980")
        return date_time


################################################################################
# Building


def patterns_list(args, patterns):
    _filter = str.strip
    if args.pattern_comments:

        def _filter(x):
            x = x.strip()
            p = re.search("^(.*?)[ \t]*(?:[ \t]{2}#.*)?$", x).group(1).rstrip()
            if p.startswith("#"):
                return
            if p:
                return p

    if isinstance(patterns, str):
        return list(filter(None, map(_filter, patterns.splitlines())))
    return patterns


class ZipContentFilter:
    """"""

    def __init__(self, args):
        self._args = args
        self._rules = None
        self._excludes = set()
        self._log = logging.getLogger("zip")

    def compile(self, patterns):
        rules = []
        for p in patterns_list(self._args, patterns):
            self._log.debug("filter pattern: %s", p)
            if p.startswith("!"):
                r = re.compile(p[1:])
                rules.append((operator.not_, r))
            else:
                r = re.compile(p)
                rules.append((None, r))
        self._rules = rules

    def reset(self):
        self._log.debug("reset filter patterns")
        self._rules = None

    def filter(self, path, prefix=None):
        path = os.path.normpath(path)
        if prefix:
            prefix = os.path.normpath(prefix)
        rules = self._rules

        def norm_path(path, root, filename=None):
            op = os.path.join(root, filename) if filename else root
            p = os.path.relpath(root, path)
            if prefix:
                p = os.path.join(prefix, p)
            if filename:
                p = os.path.normpath(os.path.join(p, filename))
                return op, p
            return op, p + os.sep

        def apply(path):
            d = True
            for r in rules:
                op, regex = r
                neg = op is operator.not_
                m = regex.fullmatch(path)
                if neg and m:
                    d = False
                elif m:
                    d = True
            if d:
                return path

        def emit_dir(dpath, opath):
            if apply(dpath):
                yield opath
            else:
                self._log.debug("skip:   %s", dpath)

        def emit_file(fpath, opath):
            if apply(fpath):
                yield opath
            else:
                self._log.debug("skip:   %s", fpath)

        if os.path.isfile(path):
            name = os.path.basename(path)
            if prefix:
                name = os.path.join(prefix, name)
            if apply(name):
                yield path
        else:
            for root, dirs, files in os.walk(path, followlinks=True):
                # Sort directories and files to ensure they are always processed in the same order
                dirs.sort()
                files.sort()
                o, d = norm_path(path, root)
                # log.info('od: %s %s', o, d)
                if root != path:
                    yield from emit_dir(d, o)
                for name in files:
                    o, f = norm_path(path, root, name)
                    # log.info('of: %s %s', o, f)
                    yield from emit_file(f, o)


def get_build_system_from_pyproject_toml(pyproject_file):
    # Implement a basic TOML parser because python stdlib does not provide toml support and we probably do not want to add external dependencies
    if os.path.isfile(pyproject_file):
        with open(pyproject_file) as f:
            bs = False
            for line in f.readlines():
                if line.startswith("[build-system]"):
                    bs = True
                    continue
                if bs and line.startswith("build-backend") and "poetry" in line:
                    return "poetry"


class BuildPlanManager:
    """"""

    def __init__(self, args, log=None):
        self._args = args
        self._source_paths = None
        self._log = log or logging.root

    def hash(self, extra_paths):
        if not self._source_paths:
            raise ValueError("BuildPlanManager.plan() should be called first")

        content_hash_paths = self._source_paths + extra_paths

        # Generate a hash based on file names and content. Also use the
        # runtime value, build command, and content of the build paths
        # because they can have an effect on the resulting archive.
        self._log.debug("Computing content hash on files...")
        content_hash = generate_content_hash(content_hash_paths, log=self._log)
        return content_hash

    def plan(self, source_path, query):
        claims = source_path
        if not isinstance(source_path, list):
            claims = [source_path]

        source_paths = []
        build_plan = []
        build_step = []

        def step(*x):
            build_step.append(x)

        def hash(path):
            source_paths.append(path)

        def pip_requirements_step(path, prefix=None, required=False, tmp_dir=None):
            command = runtime
            requirements = path
            if os.path.isdir(path):
                requirements = os.path.join(path, "requirements.txt")
            if not os.path.isfile(requirements):
                if required:
                    raise RuntimeError("File not found: {}".format(requirements))
            else:
                if not query.docker and not shutil.which(command):
                    raise RuntimeError(
                        "Python interpreter version equal "
                        "to defined lambda runtime ({}) should be "
                        "available in system PATH".format(command)
                    )

                step("pip", runtime, requirements, prefix, tmp_dir)
                hash(requirements)

        def poetry_install_step(
            path, poetry_export_extra_args=[], prefix=None, required=False, tmp_dir=None
        ):
            pyproject_file = path
            if os.path.isdir(path):
                pyproject_file = os.path.join(path, "pyproject.toml")
            if get_build_system_from_pyproject_toml(pyproject_file) != "poetry":
                if required:
                    raise RuntimeError(
                        "poetry configuration not found: {}".format(pyproject_file)
                    )
            else:
                step("poetry", runtime, path, poetry_export_extra_args, prefix, tmp_dir)
                hash(pyproject_file)
                pyproject_path = os.path.dirname(pyproject_file)
                poetry_lock_file = os.path.join(pyproject_path, "poetry.lock")
                if os.path.isfile(poetry_lock_file):
                    hash(poetry_lock_file)
                poetry_toml_file = os.path.join(pyproject_path, "poetry.toml")
                if os.path.isfile(poetry_toml_file):
                    hash(poetry_toml_file)

        def npm_requirements_step(path, prefix=None, required=False, tmp_dir=None):
            command = "npm"
            requirements = path
            if os.path.isdir(path):
                requirements = os.path.join(path, "package.json")
            if not os.path.isfile(requirements):
                if required:
                    raise RuntimeError("File not found: {}".format(requirements))
            else:
                if not query.docker and not shutil.which(command):
                    raise RuntimeError(
                        "Nodejs package manager ({}) should be "
                        "available in system PATH".format(command)
                    )

                step("npm", runtime, requirements, prefix, tmp_dir)
                hash(requirements)

        def commands_step(path, commands):
            if not commands:
                return

            if isinstance(commands, str):
                commands = map(str.strip, commands.splitlines())

            if path:
                path = os.path.normpath(path)
                step("set:workdir", path)

            batch = []
            for c in commands:
                if isinstance(c, str):
                    if c.startswith(":zip"):
                        if path:
                            hash(path)
                        if batch:
                            step("sh", "\n".join(batch))
                            batch.clear()
                        c = shlex.split(c)
                        n = len(c)
                        if n == 3:
                            _, _path, prefix = c
                            prefix = prefix.strip()
                            _path = os.path.normpath(_path)
                            step("zip:embedded", _path, prefix)
                        elif n == 2:
                            _, _path = c
                            _path = os.path.normpath(_path)
                            step("zip:embedded", _path)
                        elif n == 1:
                            step("zip:embedded")
                        else:
                            raise ValueError(
                                ":zip invalid call signature, use: "
                                "':zip [path [prefix_in_zip]]'"
                            )
                    else:
                        batch.append(c)
            if batch:
                step("sh", "\n".join(batch))
                batch.clear()

        for claim in claims:
            if isinstance(claim, str):
                path = claim
                if not os.path.exists(path):
                    abort(
                        'Could not locate source_path "{path}".  Paths are relative to directory where `terraform plan` is being run ("{pwd}")'.format(
                            path=path, pwd=os.getcwd()
                        )
                    )
                runtime = query.runtime
                if runtime.startswith("python"):
                    pip_requirements_step(os.path.join(path, "requirements.txt"))
                    poetry_install_step(path)
                elif runtime.startswith("nodejs"):
                    npm_requirements_step(os.path.join(path, "package.json"))
                step("zip", path, None)
                hash(path)

            elif isinstance(claim, dict):
                path = claim.get("path")
                patterns = claim.get("patterns")
                commands = claim.get("commands")
                if patterns:
                    step("set:filter", patterns_list(self._args, patterns))
                if commands:
                    commands_step(path, commands)
                else:
                    prefix = claim.get("prefix_in_zip")
                    pip_requirements = claim.get("pip_requirements")
                    poetry_install = claim.get("poetry_install")
                    poetry_export_extra_args = claim.get("poetry_export_extra_args", [])
                    npm_requirements = claim.get(
                        "npm_requirements", claim.get("npm_package_json")
                    )
                    runtime = claim.get("runtime", query.runtime)

                    if pip_requirements and runtime.startswith("python"):
                        if isinstance(pip_requirements, bool) and path:
                            pip_requirements_step(
                                path,
                                prefix,
                                required=True,
                                tmp_dir=claim.get("pip_tmp_dir"),
                            )
                        else:
                            pip_requirements_step(
                                pip_requirements,
                                prefix,
                                required=True,
                                tmp_dir=claim.get("pip_tmp_dir"),
                            )

                    if poetry_install and runtime.startswith("python"):
                        if path:
                            poetry_install_step(
                                path,
                                prefix=prefix,
                                poetry_export_extra_args=poetry_export_extra_args,
                                required=True,
                                tmp_dir=claim.get("poetry_tmp_dir"),
                            )

                    if npm_requirements and runtime.startswith("nodejs"):
                        if isinstance(npm_requirements, bool) and path:
                            npm_requirements_step(
                                path,
                                prefix,
                                required=True,
                                tmp_dir=claim.get("npm_tmp_dir"),
                            )
                        else:
                            npm_requirements_step(
                                npm_requirements,
                                prefix,
                                required=True,
                                tmp_dir=claim.get("npm_tmp_dir"),
                            )
                    if path:
                        path = os.path.normpath(path)
                        step("zip", path, prefix)
                        if patterns:
                            # Take patterns into account when computing hash
                            pf = ZipContentFilter(args=self._args)
                            pf.compile(patterns)

                            for path_from_pattern in pf.filter(path, prefix):
                                hash(path_from_pattern)
                        else:
                            hash(path)
            else:
                raise ValueError("Unsupported source_path item: {}".format(claim))

            if build_step:
                build_plan.append(build_step)
                build_step = []

        self._source_paths = source_paths
        return build_plan

    def execute(self, build_plan, zip_stream, query):
        sh_log = logging.getLogger("sh")

        tf_work_dir = os.getcwd()

        zs = zip_stream
        sh_work_dir = None
        pf = None

        for step in build_plan:
            # init step
            sh_work_dir = tf_work_dir
            if pf:
                pf.reset()
                pf = None

            log.debug("STEPDIR: %s", sh_work_dir)

            # execute step actions
            for action in step:
                cmd = action[0]
                if cmd.startswith("zip"):
                    ts = 0 if cmd == "zip:embedded" else None

                    source_path, prefix = None, None
                    n = len(action)
                    if n == 2:
                        source_path = action[1]
                    elif n == 3:
                        source_path, prefix = action[1:]

                    if source_path:
                        if not os.path.isabs(source_path):
                            source_path = os.path.normpath(
                                os.path.join(sh_work_dir, source_path)
                            )
                    else:
                        source_path = sh_work_dir
                    if os.path.isdir(source_path):
                        if pf:
                            self._zip_write_with_filter(
                                zs, pf, source_path, prefix, timestamp=ts
                            )
                        else:
                            zs.write_dirs(source_path, prefix=prefix, timestamp=ts)
                    else:
                        zs.write_file(source_path, prefix=prefix, timestamp=ts)
                elif cmd == "pip":
                    runtime, pip_requirements, prefix, tmp_dir = action[1:]
                    with install_pip_requirements(
                        query, pip_requirements, tmp_dir
                    ) as rd:
                        if rd:
                            if pf:
                                self._zip_write_with_filter(
                                    zs, pf, rd, prefix, timestamp=0
                                )
                            else:
                                # XXX: timestamp=0 - what actually do with it?
                                zs.write_dirs(rd, prefix=prefix, timestamp=0)
                elif cmd == "poetry":
                    (runtime, path, poetry_export_extra_args, prefix, tmp_dir) = action[
                        1:
                    ]
                    log.info("poetry_export_extra_args: %s", poetry_export_extra_args)
                    with install_poetry_dependencies(
                        query, path, poetry_export_extra_args, tmp_dir
                    ) as rd:
                        if rd:
                            if pf:
                                self._zip_write_with_filter(
                                    zs, pf, rd, prefix, timestamp=0
                                )
                            else:
                                # XXX: timestamp=0 - what actually do with it?
                                zs.write_dirs(rd, prefix=prefix, timestamp=0)
                elif cmd == "npm":
                    runtime, npm_requirements, prefix, tmp_dir = action[1:]
                    with install_npm_requirements(
                        query, npm_requirements, tmp_dir
                    ) as rd:
                        if rd:
                            if pf:
                                self._zip_write_with_filter(
                                    zs, pf, rd, prefix, timestamp=0
                                )
                            else:
                                # XXX: timestamp=0 - what actually do with it?
                                zs.write_dirs(rd, prefix=prefix, timestamp=0)
                elif cmd == "sh":
                    with tempfile.NamedTemporaryFile(
                        mode="w+t", delete=True
                    ) as temp_file:
                        script = action[1]

                        if log.isEnabledFor(DEBUG2):
                            log.debug("exec shell script ...")
                            for line in script.splitlines():
                                sh_log.debug(line)

                        script = "\n".join(
                            (
                                script,
                                # NOTE: Execute `pwd` to determine the subprocess shell's
                                # working directory after having executed all other commands.
                                "retcode=$?",
                                f"pwd >{temp_file.name}",
                                "exit $retcode",
                            )
                        )

                        p = subprocess.Popen(
                            script,
                            shell=True,
                            stdout=subprocess.PIPE,
                            stderr=subprocess.PIPE,
                            cwd=sh_work_dir,
                        )

                        call_stdout, call_stderr = p.communicate()
                        exit_code = p.returncode
                        log.debug("exit_code: %s", exit_code)
                        if exit_code != 0:
                            raise RuntimeError(
                                "Script did not run successfully, exit code {}: {} - {}".format(
                                    exit_code,
                                    call_stdout.decode("utf-8").strip(),
                                    call_stderr.decode("utf-8").strip(),
                                )
                            )

                        temp_file.seek(0)
                        # NOTE: This var `sh_work_dir` is consumed in cmd == "zip" loop
                        sh_work_dir = temp_file.read().strip()
                        log.debug("WORKDIR: %s", sh_work_dir)

                elif cmd == "set:workdir":
                    path = action[1]
                    sh_work_dir = os.path.normpath(os.path.join(tf_work_dir, path))
                    log.debug("WORKDIR: %s", sh_work_dir)

                elif cmd == "set:filter":
                    patterns = action[1]
                    pf = ZipContentFilter(args=self._args)
                    pf.compile(patterns)

    @staticmethod
    def _zip_write_with_filter(
        zip_stream, path_filter, source_path, prefix, timestamp=None
    ):
        for path in path_filter.filter(source_path, prefix):
            if os.path.isdir(source_path):
                arcname = os.path.relpath(path, source_path)
            else:
                arcname = os.path.basename(path)
            zip_stream.write_file(path, prefix, arcname, timestamp=timestamp)


@contextmanager
def install_pip_requirements(query, requirements_file, tmp_dir):
    # TODO:
    #  1. Emit files instead of temp_dir

    if not os.path.exists(requirements_file):
        yield
        return

    runtime = query.runtime
    artifacts_dir = query.artifacts_dir
    docker = query.docker
    temp_dir = query.temp_dir
    docker_image_tag_id = None

    if docker:
        docker_file = docker.docker_file
        docker_image = docker.docker_image
        docker_build_root = docker.docker_build_root

        if docker_image:
            ok = False
            while True:
                output = check_output(docker_image_id_command(docker_image))
                if output:
                    docker_image_tag_id = output.decode().strip()
                    log.debug(
                        "DOCKER TAG ID: %s -> %s", docker_image, docker_image_tag_id
                    )
                    ok = True
                if ok:
                    break
                docker_cmd = docker_build_command(
                    build_root=docker_build_root,
                    docker_file=docker_file,
                    tag=docker_image,
                )
                check_call(docker_cmd)
                ok = True
        elif docker_file or docker_build_root:
            raise ValueError(
                "docker_image must be specified " "for a custom image future references"
            )

    working_dir = os.getcwd()

    log.info("Installing python requirements: %s", requirements_file)
    with tempdir(tmp_dir) as temp_dir:
        requirements_filename = os.path.basename(requirements_file)
        target_file = os.path.join(temp_dir, requirements_filename)
        shutil.copyfile(requirements_file, target_file)

        python_exec = runtime
        subproc_env = None

        if not docker:
            if WINDOWS:
                python_exec = "python.exe"
            elif OSX:
                # Workaround for OSX when XCode command line tools'
                # python becomes the main system python interpreter
                os_path = "{}:/Library/Developer/CommandLineTools" "/usr/bin".format(
                    os.environ["PATH"]
                )
                subproc_env = os.environ.copy()
                subproc_env["PATH"] = os_path

        # Install dependencies into the temporary directory.
        with cd(temp_dir):
            pip_command = [
                python_exec,
                "-m",
                "pip",
                "install",
                "--no-compile",
                "--prefix=",
                "--target=.",
                "--requirement={}".format(requirements_filename),
            ]
            if docker:
                with_ssh_agent = docker.with_ssh_agent
                pip_cache_dir = docker.docker_pip_cache
                if pip_cache_dir:
                    if isinstance(pip_cache_dir, str):
                        pip_cache_dir = os.path.abspath(
                            os.path.join(working_dir, pip_cache_dir)
                        )
                    else:
                        pip_cache_dir = os.path.abspath(
                            os.path.join(working_dir, artifacts_dir, "cache/pip")
                        )

                chown_mask = "{}:{}".format(os.getuid(), os.getgid())
                shell_command = [
                    shlex_join(pip_command),
                    "&&",
                    shlex_join(["chown", "-R", chown_mask, "."]),
                ]
                shell_command = [" ".join(shell_command)]
                check_call(
                    docker_run_command(
                        ".",
                        shell_command,
                        runtime,
                        image=docker_image_tag_id,
                        shell=True,
                        ssh_agent=with_ssh_agent,
                        pip_cache_dir=pip_cache_dir,
                        docker=docker,
                    )
                )
            else:
                cmd_log.info(shlex_join(pip_command))
                log_handler and log_handler.flush()
                try:
                    check_call(pip_command, env=subproc_env)
                except FileNotFoundError as e:
                    raise RuntimeError(
                        "Python interpreter version equal "
                        "to defined lambda runtime ({}) should be "
                        "available in system PATH".format(runtime)
                    ) from e

            os.remove(target_file)
            yield temp_dir


@contextmanager
def install_poetry_dependencies(query, path, poetry_export_extra_args, tmp_dir):
    # TODO:
    #  1. Emit files instead of temp_dir

    # pyproject.toml is always required by poetry
    pyproject_file = path
    if os.path.isdir(path):
        pyproject_file = os.path.join(path, "pyproject.toml")
    if not os.path.exists(pyproject_file):
        yield
        return

    # poetry.lock & poetry.toml are optional
    pyproject_path = os.path.dirname(pyproject_file)
    poetry_lock_file = os.path.join(pyproject_path, "poetry.lock")
    poetry_toml_file = os.path.join(pyproject_path, "poetry.toml")

    runtime = query.runtime
    artifacts_dir = query.artifacts_dir
    docker = query.docker
    docker_image_tag_id = None

    if docker:
        docker_file = docker.docker_file
        docker_image = docker.docker_image
        docker_build_root = docker.docker_build_root

        if docker_image:
            ok = False
            while True:
                output = check_output(docker_image_id_command(docker_image))
                if output:
                    docker_image_tag_id = output.decode().strip()
                    log.debug(
                        "DOCKER TAG ID: %s -> %s", docker_image, docker_image_tag_id
                    )
                    ok = True
                if ok:
                    break
                docker_cmd = docker_build_command(
                    build_root=docker_build_root,
                    docker_file=docker_file,
                    tag=docker_image,
                )
                check_call(docker_cmd)
                ok = True
        elif docker_file or docker_build_root:
            raise ValueError(
                "docker_image must be specified for a custom image future references"
            )

    working_dir = os.getcwd()

    log.info("Installing python dependencies with poetry & pip: %s", poetry_lock_file)
    with tempdir(tmp_dir) as temp_dir:

        def copy_file_to_target(file, temp_dir):
            filename = os.path.basename(file)
            target_file = os.path.join(temp_dir, filename)
            shutil.copyfile(file, target_file)
            return target_file

        pyproject_target_file = copy_file_to_target(pyproject_file, temp_dir)

        if os.path.isfile(poetry_lock_file):
            log.info("Using poetry.lock file: %s", poetry_lock_file)
            poetry_lock_target_file = copy_file_to_target(poetry_lock_file, temp_dir)
        else:
            poetry_lock_target_file = None

        if os.path.isfile(poetry_toml_file):
            log.info("Using poetry.toml configuration file: %s", poetry_toml_file)
            poetry_toml_target_file = copy_file_to_target(poetry_toml_file, temp_dir)
        else:
            poetry_toml_target_file = None

        poetry_exec = "poetry"
        python_exec = runtime
        subproc_env = None

        if not docker:
            if WINDOWS:
                poetry_exec = "poetry.bat"

        # Install dependencies into the temporary directory.
        with cd(temp_dir):
            # NOTE: poetry must be available in the build environment, which is the case with lambci/lambda:build-python* docker images but not public.ecr.aws/sam/build-python* docker images
            # FIXME: poetry install does not currently allow to specify the target directory so we export the
            # requirements then install them with "pip --no-deps" to avoid using pip dependency resolver

            poetry_export = [
                poetry_exec,
                "export",
                "--format",
                "requirements.txt",
                "--output",
                "requirements.txt",
                "--with-credentials",
            ] + poetry_export_extra_args

            poetry_commands = [
                [
                    poetry_exec,
                    "config",
                    "--no-interaction",
                    "virtualenvs.create",
                    "true",
                ],
                [
                    poetry_exec,
                    "config",
                    "--no-interaction",
                    "virtualenvs.in-project",
                    "true",
                ],
                poetry_export,
                [
                    python_exec,
                    "-m",
                    "pip",
                    "install",
                    "--no-compile",
                    "--no-deps",
                    "--prefix=",
                    "--target=.",
                    "--requirement=requirements.txt",
                ],
            ]
            if docker:
                with_ssh_agent = docker.with_ssh_agent
                poetry_cache_dir = docker.docker_poetry_cache
                if poetry_cache_dir:
                    if isinstance(poetry_cache_dir, str):
                        poetry_cache_dir = os.path.abspath(
                            os.path.join(working_dir, poetry_cache_dir)
                        )
                    else:
                        poetry_cache_dir = os.path.abspath(
                            os.path.join(working_dir, artifacts_dir, "cache/poetry")
                        )

                chown_mask = "{}:{}".format(os.getuid(), os.getgid())
                poetry_commands += [["chown", "-R", chown_mask, "."]]
                shell_commands = [
                    shlex_join(poetry_command) for poetry_command in poetry_commands
                ]
                shell_command = [" && ".join(shell_commands)]
                check_call(
                    docker_run_command(
                        ".",
                        shell_command,
                        runtime,
                        image=docker_image_tag_id,
                        shell=True,
                        ssh_agent=with_ssh_agent,
                        poetry_cache_dir=poetry_cache_dir,
                        docker=docker,
                    )
                )
            else:
                cmd_log.info(poetry_commands)
                log_handler and log_handler.flush()
                for poetry_command in poetry_commands:
                    check_call(poetry_command, env=subproc_env)

            os.remove(pyproject_target_file)
            if poetry_lock_target_file:
                os.remove(poetry_lock_target_file)
            if poetry_toml_target_file:
                os.remove(poetry_toml_target_file)

            yield temp_dir


@contextmanager
def install_npm_requirements(query, requirements_file, tmp_dir):
    # TODO:
    #  1. Emit files instead of temp_dir

    if not os.path.exists(requirements_file):
        yield
        return

    runtime = query.runtime
    artifacts_dir = query.artifacts_dir
    temp_dir = query.temp_dir
    docker = query.docker
    docker_image_tag_id = None

    if docker:
        docker_file = docker.docker_file
        docker_image = docker.docker_image
        docker_build_root = docker.docker_build_root

        if docker_image:
            ok = False
            while True:
                output = check_output(docker_image_id_command(docker_image))
                if output:
                    docker_image_tag_id = output.decode().strip()
                    log.debug(
                        "DOCKER TAG ID: %s -> %s", docker_image, docker_image_tag_id
                    )
                    ok = True
                if ok:
                    break
                docker_cmd = docker_build_command(
                    build_root=docker_build_root,
                    docker_file=docker_file,
                    tag=docker_image,
                )
                check_call(docker_cmd)
                ok = True
        elif docker_file or docker_build_root:
            raise ValueError(
                "docker_image must be specified " "for a custom image future references"
            )

    log.info("Installing npm requirements: %s", requirements_file)
    with tempdir(tmp_dir) as temp_dir:
        requirements_filename = os.path.basename(requirements_file)
        target_file = os.path.join(temp_dir, requirements_filename)
        shutil.copyfile(requirements_file, target_file)

        subproc_env = None
        npm_exec = "npm"
        if not docker:
            if WINDOWS:
                npm_exec = "npm.cmd"
            elif OSX:
                subproc_env = os.environ.copy()

        # Install dependencies into the temporary directory.
        with cd(temp_dir):
            npm_command = [npm_exec, "install"]
            if docker:
                with_ssh_agent = docker.with_ssh_agent
                chown_mask = "{}:{}".format(os.getuid(), os.getgid())
                shell_command = [
                    shlex_join(npm_command),
                    "&&",
                    shlex_join(["chown", "-R", chown_mask, "."]),
                ]
                shell_command = [" ".join(shell_command)]
                check_call(
                    docker_run_command(
                        ".",
                        shell_command,
                        runtime,
                        image=docker_image_tag_id,
                        shell=True,
                        ssh_agent=with_ssh_agent,
                        docker=docker,
                    )
                )
            else:
                cmd_log.info(shlex_join(npm_command))
                log_handler and log_handler.flush()
                try:
                    check_call(npm_command, env=subproc_env)
                except FileNotFoundError as e:
                    raise RuntimeError(
                        "Nodejs interpreter version equal "
                        "to defined lambda runtime ({}) should be "
                        "available in system PATH".format(runtime)
                    ) from e

            os.remove(target_file)
            yield temp_dir


def docker_image_id_command(tag):
    """"""
    docker_cmd = ["docker", "images", "--format={{.ID}}", tag]
    cmd_log.info(shlex_join(docker_cmd))
    log_handler and log_handler.flush()
    return docker_cmd


def docker_build_command(tag=None, docker_file=None, build_root=False):
    """"""
    if not (build_root or docker_file):
        raise ValueError("docker_build_root or docker_file must be provided")

    docker_cmd = ["docker", "build"]

    if tag:
        docker_cmd.extend(["--tag", tag])
    else:
        raise ValueError("docker_image must be specified")
    if not build_root:
        build_root = os.path.dirname(docker_file)
    if docker_file:
        docker_cmd.extend(["--file", docker_file])
    docker_cmd.append(build_root)

    cmd_log.info(shlex_join(docker_cmd))
    log_handler and log_handler.flush()
    return docker_cmd


def docker_run_command(
    build_root,
    command,
    runtime,
    image=None,
    shell=None,
    ssh_agent=False,
    interactive=False,
    pip_cache_dir=None,
    poetry_cache_dir=None,
    docker=None,
):
    """"""
    if platform.system() not in ("Linux", "Darwin"):
        raise RuntimeError("Unsupported platform for docker building")

    workdir = "/var/task"

    docker_cmd = ["docker", "run", "--rm", "-w", workdir]

    if interactive:
        docker_cmd.append("-it")

    bind_path = os.path.abspath(build_root)
    docker_cmd.extend(["-v", "{}:{}:z".format(bind_path, workdir)])

    home = os.environ["HOME"]
    docker_cmd.extend(
        [
            # '-v', '{}/.ssh/id_rsa:/root/.ssh/id_rsa:z'.format(home),
            "-v",
            "{}/.ssh/known_hosts:/root/.ssh/known_hosts:z".format(home),
        ]
    )

    if docker and docker.docker_additional_options:
        docker_cmd.extend(docker.docker_additional_options)

    if ssh_agent:
        if platform.system() == "Darwin":
            # https://docs.docker.com/docker-for-mac/osxfs/#ssh-agent-forwarding
            docker_cmd.extend(
                [
                    "--mount",
                    "type=bind,"
                    "src=/run/host-services/ssh-auth.sock,"
                    "target=/run/host-services/ssh-auth.sock",
                    "-e",
                    "SSH_AUTH_SOCK=/run/host-services/ssh-auth.sock",
                ]
            )
        elif platform.system() == "Linux":
            sock = os.environ["SSH_AUTH_SOCK"]  # TODO: Handle missing env var
            docker_cmd.extend(
                [
                    "-v",
                    "{}:/tmp/ssh_sock:z".format(sock),
                    "-e",
                    "SSH_AUTH_SOCK=/tmp/ssh_sock",
                ]
            )

    if platform.system() in ("Linux", "Darwin"):
        if pip_cache_dir:
            pip_cache_dir = os.path.abspath(pip_cache_dir)
            docker_cmd.extend(
                [
                    "-v",
                    "{}:/root/.cache/pip:z".format(pip_cache_dir),
                ]
            )
        if poetry_cache_dir:
            poetry_cache_dir = os.path.abspath(poetry_cache_dir)
            docker_cmd.extend(
                [
                    "-v",
                    "{}:/root/.cache/pypoetry:z".format(poetry_cache_dir),
                ]
            )

    if not image:
        image = "public.ecr.aws/sam/build-{}".format(runtime)

    if docker and docker.docker_entrypoint:
        docker_cmd.extend(["--entrypoint", docker.docker_entrypoint])
    else:
        docker_cmd.extend(["--entrypoint", ""])

    docker_cmd.append(image)

    assert isinstance(command, list)
    if shell:
        if not isinstance(shell, str):
            shell = "/bin/sh"
        docker_cmd.extend([shell, "-c"])
    docker_cmd.extend(command)

    cmd_log.info(shlex_join(docker_cmd))
    log_handler and log_handler.flush()
    return docker_cmd


################################################################################
# Commands


def prepare_command(args):
    """
    Generates a content hash of the source_path, which is used to determine if
    the Lambda code has changed, ignoring file modification and access times.

    Outputs a filename and a command to run if the archive needs to be built.
    """

    log = logging.getLogger("prepare")

    # Load the query.
    query_data = json.load(sys.stdin)

    dump_env()
    if log.isEnabledFor(DEBUG2):
        if log.isEnabledFor(DEBUG3):
            log.debug("QUERY: %s", json.dumps(query_data, indent=2))
        else:
            log_excludes = ("source_path", "hash_extra_paths", "paths")
            qd = {k: v for k, v in query_data.items() if k not in log_excludes}
            log.debug("QUERY (excerpt): %s", json.dumps(qd, indent=2))

    query = datatree("prepare_query", **query_data)

    tf_paths = query.paths
    runtime = query.runtime
    function_name = query.function_name
    artifacts_dir = query.artifacts_dir
    hash_extra_paths = query.hash_extra_paths
    source_path = query.source_path
    hash_extra = query.hash_extra
    recreate_missing_package = yesno_bool(
        args.recreate_missing_package
        if args.recreate_missing_package is not None
        else query.recreate_missing_package
    )
    docker = query.docker

    bpm = BuildPlanManager(args, log=log)
    build_plan = bpm.plan(source_path, query)

    if log.isEnabledFor(DEBUG2):
        log.debug("BUILD_PLAN: %s", json.dumps(build_plan, indent=2))

    # Expand a Terraform path.<cwd|root|module> references
    hash_extra_paths = [p.format(path=tf_paths) for p in hash_extra_paths]

    content_hash = bpm.hash(hash_extra_paths)
    content_hash.update(json.dumps(build_plan, sort_keys=True).encode())
    content_hash.update(runtime.encode())
    content_hash.update(hash_extra.encode())
    content_hash = content_hash.hexdigest()

    # Generate a unique filename based on the hash.
    zip_filename = os.path.join(artifacts_dir, "{}.zip".format(content_hash))

    # Compute timestamp trigger
    was_missing = False
    filename_path = os.path.join(os.getcwd(), zip_filename)
    if recreate_missing_package:
        if os.path.exists(filename_path):
            st = os.stat(filename_path)
            timestamp = st.st_mtime_ns
        else:
            timestamp = timestamp_now_ns()
            was_missing = True
    else:
        timestamp = "<WARNING: Missing lambda zip artifacts " "wouldn't be restored>"

    # Replace variables in the build command with calculated values.
    build_data = {
        "filename": zip_filename,
        "runtime": runtime,
        "artifacts_dir": artifacts_dir,
        "build_plan": build_plan,
    }
    if docker:
        build_data["docker"] = docker

    build_plan = json.dumps(build_data)
    build_plan_filename = os.path.join(
        artifacts_dir, "{}.plan.json".format(content_hash)
    )
    if not os.path.exists(artifacts_dir):
        os.makedirs(artifacts_dir, exist_ok=True)
    with open(build_plan_filename, "w") as f:
        f.write(build_plan)

    # Output the result to Terraform.
    json.dump(
        {
            "filename": zip_filename,
            "build_plan": build_plan,
            "build_plan_filename": build_plan_filename,
            "timestamp": str(timestamp),
            "was_missing": "true" if was_missing else "false",
        },
        sys.stdout,
        indent=2,
    )
    sys.stdout.write("\n")


def build_command(args):
    """
    Builds a zip file from the source_dir or source_file.
    Installs dependencies with pip or npm automatically.
    """

    log = logging.getLogger("build")

    dump_env()
    if log.isEnabledFor(DEBUG2):
        log.debug("CMD: python3 %s", shlex_join(sys.argv))

    with open(args.build_plan_file) as f:
        query_data = json.load(f)
    query = datatree("build_query", **query_data)

    runtime = query.runtime
    filename = query.filename
    build_plan = query.build_plan
    _timestamp = args.zip_file_timestamp

    timestamp = 0
    if _timestamp.isnumeric():
        timestamp = int(_timestamp)

    if os.path.exists(filename) and not args.force:
        log.info("Reused: %s", shlex.quote(filename))
        return

    # Zip up the build plan and write it to the target filename.
    # This will be used by the Lambda function as the source code package.
    with ZipWriteStream(filename) as zs:
        bpm = BuildPlanManager(args, log=log)
        bpm.execute(build_plan, zs, query)

    os.utime(filename, ns=(timestamp, timestamp))
    log.info("Created: %s", shlex.quote(filename))
    if log.isEnabledFor(logging.DEBUG):
        with open(filename, "rb") as f:
            log.info("Base64sha256: %s", source_code_hash(f.read()))


def add_hidden_commands(sub_parsers):
    sp = sub_parsers

    def hidden_parser(name, **kwargs):
        p = sp.add_parser(name, **kwargs)
        sp._choices_actions.pop()  # XXX: help=argparse.SUPPRESS - doesn't work
        return p

    p = hidden_parser("docker", help="Run docker build")
    p.set_defaults(
        command=lambda args: subprocess.call(
            docker_run_command(
                args.build_root, args.docker_command, args.runtime, interactive=True
            )
        )
    )
    p.add_argument("build_root", help="A docker build root folder")
    p.add_argument(
        "docker_command",
        help="A docker container command",
        metavar="command",
        nargs=argparse.REMAINDER,
    )
    p.add_argument(
        "-r", "--runtime", help="A docker image runtime", default="python3.12"
    )

    p = hidden_parser("docker-image", help="Run docker build")
    p.set_defaults(
        command=lambda args: subprocess.call(
            docker_build_command(args.build_root, args.docker_file, args.tag)
        )
    )
    p.add_argument("-t", "--tag", help="A docker image tag")
    p.add_argument("build_root", help="A docker build root folder")
    p.add_argument("docker_file", help="A docker file path", nargs=argparse.OPTIONAL)

    def zip_cmd(args):
        if args.verbose:
            log.setLevel(logging.DEBUG)
        with ZipWriteStream(args.zipfile) as zs:
            zs.write_dirs(*args.dir, timestamp=args.timestamp)
        if log.isEnabledFor(logging.DEBUG):
            zipinfo = shutil.which("zipinfo")
            if zipinfo:
                log.debug("-" * 80)
                subprocess.call([zipinfo, args.zipfile])
            log.debug("-" * 80)
            log.debug(
                "Source code hash: %s",
                source_code_hash(open(args.zipfile, "rb").read()),
            )

    p = hidden_parser("zip", help="Zip folder with provided files timestamp")
    p.set_defaults(command=zip_cmd)
    p.add_argument("zipfile", help="Path to a zip file")
    p.add_argument(
        "dir", nargs=argparse.ONE_OR_MORE, help="Path to a directory for packaging"
    )
    p.add_argument(
        "-t",
        "--timestamp",
        type=int,
        help="A timestamp to override for all zip members",
    )
    p.add_argument("-v", "--verbose", action="store_true")

    p = hidden_parser("hash", help="Generate content hash for a file")
    p.set_defaults(command=lambda args: print(source_code_hash(args.file.read())))
    p.add_argument("file", help="Path to a file", type=argparse.FileType("rb"))


def args_parser():
    ap = argparse.ArgumentParser()
    ap.set_defaults(command=lambda _: ap.print_usage())
    sp = ap.add_subparsers(metavar="COMMAND")

    p = sp.add_parser("prepare", help="compute a filename hash for a zip archive")
    p.set_defaults(command=prepare_command)

    p = sp.add_parser("build", help="build and pack to a zip archive")
    p.set_defaults(command=build_command)
    p.add_argument(
        "--force",
        action="store_true",
        help="Force rebuilding even if a zip artifact exists",
    )
    p.add_argument(
        "-t",
        "--timestamp",
        dest="zip_file_timestamp",
        required=True,
        help="A zip file timestamp generated by the prepare command",
    )
    p.add_argument(
        "build_plan_file",
        metavar="PLAN_FILE",
        help="A build plan file provided by the prepare command",
    )
    add_hidden_commands(sp)
    return ap


def main():
    ns = argparse.Namespace(
        pattern_comments=yesno_bool(
            os.environ.get("TF_LAMBDA_PACKAGE_PATTERN_COMMENTS", False)
        ),
        recreate_missing_package=os.environ.get(
            "TF_RECREATE_MISSING_LAMBDA_PACKAGE", None
        ),
        log_level=os.environ.get("TF_LAMBDA_PACKAGE_LOG_LEVEL", "INFO"),
    )

    p = args_parser()
    args = p.parse_args(namespace=ns)

    if args.command is prepare_command:
        configure_logging(use_tf_stderr=True)
    else:
        configure_logging()

    if args.log_level:
        ll = logging._nameToLevel.get(args.log_level)
        if ll and logging._checkLevel(ll):
            logging.root.setLevel(args.log_level)

    exit(args.command(args))


if __name__ == "__main__":
    main()
```

## File: ./iac/.terraform/modules/lambda/tests/fixtures/node-app/index.js
```javascript
// test
```

## File: ./iac/.terraform/modules/lambda/tests/test_package_toml.py
```python
from package import get_build_system_from_pyproject_toml, BuildPlanManager
from pytest import raises
from unittest.mock import Mock


def test_get_build_system_from_pyproject_toml_inexistent():
    assert (
        get_build_system_from_pyproject_toml("fixtures/inexistent/pyproject.toml")
        is None
    )


def test_get_build_system_from_pyproject_toml_unknown():
    assert (
        get_build_system_from_pyproject_toml("fixtures/pyproject-unknown.toml") is None
    )


def test_build_manager_sucess_command():
    bpm = BuildPlanManager(args=Mock())
    # Should not have exception raised
    bpm.execute(build_plan=[["sh", "/tmp", "pwd"]], zip_stream=None, query=None)


def test_build_manager_failing_command():
    bpm = BuildPlanManager(args=Mock())
    with raises(Exception):
        bpm.execute(
            build_plan=[[["sh", "/tmp", "NOTACOMMAND"]]],
            zip_stream=None,
            query=None,
        )


def test_get_build_system_from_pyproject_toml_poetry():
    assert (
        get_build_system_from_pyproject_toml(
            "examples/fixtures/python-app-poetry/pyproject.toml"
        )
        == "poetry"
    )
```

## File: ./iac/.terraform/modules/lambda/tests/test_zip_source.py
```python
import os
from unittest.mock import MagicMock, Mock

from package import BuildPlanManager


def test_zip_source_path_sh_work_dir():
    zs = Mock()
    zs.write_dirs = MagicMock()

    bpm = BuildPlanManager(args=Mock())

    bpm.execute(
        build_plan=[
            [
                ["sh", "cd $(mktemp -d)\n echo pip install"],
                ["zip:embedded", ".", "./python"],
            ]
        ],
        zip_stream=zs,
        query=None,
    )

    zs.write_dirs.assert_called_once()

    zip_source_path = zs.write_dirs.call_args_list[0][0][0]
    assert zip_source_path != f"{os.getcwd()}"


def test_zip_source_path():
    zs = Mock()
    zs.write_dirs = MagicMock()

    bpm = BuildPlanManager(args=Mock())

    bpm.execute(
        build_plan=[
            [
                ["sh", "echo pip install"],
                ["zip:embedded", ".", "./python"],
            ]
        ],
        zip_stream=zs,
        query=None,
    )

    zs.write_dirs.assert_called_once()

    zip_source_path = zs.write_dirs.call_args_list[0][0][0]
    assert zip_source_path == f"{os.getcwd()}"
```

## File: ./jest.config.js
```javascript
/** @type {import('jest').Config} */
export default {
  // Use the ESM-aware preset
  preset: 'ts-jest/presets/default-esm',
  testEnvironment: 'node',
  extensionsToTreatAsEsm: ['.ts'],

  // Let ts-jest read the real tsconfig instead of an inline override
  injectGlobals: true,
  transform: {
    '^.+\\.ts$': [
      'ts-jest',
      {
        useESM: true,
        tsconfig: './tsconfig.jest.json'
      }
    ]
  },
  moduleNameMapper: {
    // keep relative imports intact (e.g., './foo.js' → './foo')
    '^(\\.{1,2}/.*)\\.js$': '$1'
  },
  roots: ['<rootDir>/src', '<rootDir>/test'],
  testMatch: ['**/test/unit/**/*.test.ts', '**/test/unit/**/*.spec.ts'],
  moduleFileExtensions: ['ts', 'tsx', 'js', 'jsx', 'json', 'node'],
  collectCoverageFrom: [
    'src/**/*.{ts,tsx}',
    '!src/main.ts',
    '!src/**/entities/*.ts',
    '!src/**/dtos/*.ts',
    '!src/**/migrations/**',
    '!src/**/*.module.ts',
    '!src/logging/request-id.middleware.ts',
    '!src/health/*.ts',
    '!src/app.module.ts'
  ],
  coverageThreshold: {
    global: {
      branches: 89,
      functions: 89,
      lines: 89,
      statements: 89
    }
  }
};```

## File: ./src/handlers/create.ts
```typescript
/**
 * App: Customer API
 * Package: handlers
 * File: create.ts
 * Version: 0.1.2
 * Author: Codex
 * Date: 2025-06-25T19:30:00Z
 * Description: Lambda handler to create a new CustomerProfile item, with basic parsing and validation.
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import { parseJson } from "../utils/parser";
import { validateCustomerProfile } from "../utils/validation";
import { CrudService } from "../services/crud_service";

const service = new CrudService();

export const handler = async (
  event: APIGatewayProxyEventV2,
  context: Context,
): Promise<APIGatewayProxyResult> => {
  console.log(event);
  let raw: unknown;
  try {
    raw = parseJson(event);
  } catch (err) {
    console.error("Invalid JSON in request body:", err, "body:", event);
    return { statusCode: 400, body: "Invalid JSON" };
  }

  // 2) Validate against schema
  let payload;
  try {
    payload = validateCustomerProfile(raw);
  } catch (err) {
    console.error("Validation failed:", err);
    return { statusCode: 422, body: "Validation error" };
  }

  // 3) Determine target table name
  const tableName = process.env.TABLE_NAME;
  if (!tableName) {
    console.error("TABLE_NAME environment variable is not set");
    return { statusCode: 500, body: "Server configuration error" };
  }

  // 4) Attempt creation in DynamoDB
  let created;
  try {
    created = await service.create(payload);
  } catch (err) {
    console.error("Error writing to DynamoDB:", err);
    return { statusCode: 500, body: "Internal server error" };
  }

  // 5) Return successful response
  return {
    statusCode: 201,
    body: JSON.stringify(created),
  };
};
```

## File: ./src/handlers/delete.ts
```typescript
/**
 * App: Customer API
 * Package: handlers
 * File: delete.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Lambda handler to delete a CustomerProfile item by id.
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import logger from "../utils/logger.js";
import { metrics, MetricUnit } from "../utils/metrics.js";
import tracer from "../utils/tracer.js";
import { CrudService } from "../services/crud_service.js";

const service = new CrudService();

export const handler = (tracer.captureLambdaHandler as any)(
  async (
    event: APIGatewayProxyEventV2,
    context: Context,
  ): Promise<APIGatewayProxyResult> => {
    logger.addContext(context);
    const id = event.pathParameters?.id as string;
    await service.delete(id);
    metrics.addMetric("DeleteSuccess", MetricUnit.Count, 1);
    return {
      statusCode: 204,
      body: "",
    };
  },
);
```

## File: ./src/handlers/get.ts
```typescript
/**
 * @application Serverless CRUD API
 * @source src/handlers/get.ts
 * @author Bobwares
 * @version 0.1.1
 * @description Lambda handler for retrieving a single entity by ID (GET /{id}).
 * @updated 2025-06-26T20:04:00Z
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import logger from "../utils/logger";
import { metrics, MetricUnit } from "../utils/metrics";
import { CrudService } from "../services/crud_service";

interface GetResponse {
  statusCode: number;
  headers: { [key: string]: string };
  body: string;
}

const createResponse = (
  statusCode: number,
  body: object,
  errorId?: string,
): GetResponse => ({
  statusCode,
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(errorId ? { ...body, errorId } : body),
});

const validateId = (id: unknown): id is string => {
  return typeof id === "string" && id.trim() !== "";
};

export const createHandler =
  (service: CrudService) =>
  async (
    event: APIGatewayProxyEventV2,
    context: Context,
  ): Promise<APIGatewayProxyResult> => {
    logger.addContext(context);
    logger.debug(event);
    try {
      const id = event.pathParameters?.id;
      if (!validateId(id)) {
        logger.error("Missing or invalid id in path parameters", { event });
        metrics.addMetric("GetInvalidId", MetricUnit.Count, 1);
        return createResponse(400, {
          message: "Missing or invalid id parameter",
        });
      }

      const result = await service.get(id);

      if (result) {
        metrics.addMetric("GetSuccess", MetricUnit.Count, 1);
        return createResponse(200, result);
      } else {
        metrics.addMetric("GetNotFound", MetricUnit.Count, 1);
        return createResponse(404, { message: "Not Found" });
      }
    } catch (error) {
      const errorId = context.awsRequestId;
      logger.error("Error in get handler", { error, errorId });
      metrics.addMetric("GetError", MetricUnit.Count, 1);
      return createResponse(500, { message: "Internal Server Error" }, errorId);
    } finally {
      // Publish metrics if required by the metrics utility
      // await metrics.publishStoredMetrics();
    }
  };

export const handler = createHandler(new CrudService());
```

## File: ./src/handlers/list.ts
```typescript
/**
 * App: Customer API
 * Package: handlers
 * File: list.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Lambda handler to list all CustomerProfile items.
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import logger from "../utils/logger.js";
import { metrics, MetricUnit } from "../utils/metrics.js";
import tracer from "../utils/tracer.js";
import { CrudService } from "../services/crud_service.js";

const service = new CrudService();

export const handler = (tracer.captureLambdaHandler as any)(
  async (
    _event: APIGatewayProxyEventV2,
    context: Context,
  ): Promise<APIGatewayProxyResult> => {
    logger.addContext(context);
    const items = await service.list();
    metrics.addMetric("ListSuccess", MetricUnit.Count, 1);
    return {
      statusCode: 200,
      body: JSON.stringify(items),
    };
  },
);
```

## File: ./src/handlers/patch.ts
```typescript
/**
 * App: Customer API
 * Package: handlers
 * File: patch.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Lambda handler to partially update a CustomerProfile.
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import logger from "../utils/logger.js";
import { metrics, MetricUnit } from "../utils/metrics.js";
import tracer from "../utils/tracer.js";
import { parseJson } from "../utils/parser.js";
import { validatePartialCustomerProfile } from "../utils/validation.js";
import { CrudService } from "../services/crud_service.js";

const service = new CrudService();

export const handler = (tracer.captureLambdaHandler as any)(
  async (
    event: APIGatewayProxyEventV2,
    context: Context,
  ): Promise<APIGatewayProxyResult> => {
    logger.addContext(context);
    const id = event.pathParameters?.id as string;
    const payload = validatePartialCustomerProfile(parseJson(event));
    const result = await service.patch(id, payload);
    metrics.addMetric("PatchSuccess", MetricUnit.Count, 1);
    return {
      statusCode: 200,
      body: JSON.stringify(result),
    };
  },
);
```

## File: ./src/handlers/update.ts
```typescript
/**
 * App: Customer API
 * Package: handlers
 * File: update.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Lambda handler to fully replace an existing CustomerProfile.
 */

import {
  APIGatewayProxyEventV2,
  APIGatewayProxyResult,
  Context,
} from "aws-lambda";
import logger from "../utils/logger.js";
import { metrics, MetricUnit } from "../utils/metrics.js";
import tracer from "../utils/tracer.js";
import { parseJson } from "../utils/parser.js";
import { validateCustomerProfile } from "../utils/validation.js";
import { CrudService } from "../services/crud_service.js";

const service = new CrudService();

export const handler = (tracer.captureLambdaHandler as any)(
  async (
    event: APIGatewayProxyEventV2,
    context: Context,
  ): Promise<APIGatewayProxyResult> => {
    logger.addContext(context);
    const payload = validateCustomerProfile(parseJson(event));
    const result = await service.update(payload);
    metrics.addMetric("UpdateSuccess", MetricUnit.Count, 1);
    return {
      statusCode: 200,
      body: JSON.stringify(result),
    };
  },
);
```

## File: ./src/services/crud_service.ts
```typescript
/**
 * App: Customer API
 * Package: services
 * File: crud_service.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Business logic and DynamoDB data access layer implementing
 *              CRUD operations for CustomerProfile items.
 */

import { DynamoDBClient } from "@aws-sdk/client-dynamodb";
import {
  DynamoDBDocumentClient,
  PutCommand,
  GetCommand,
  UpdateCommand,
  DeleteCommand,
  ScanCommand,
} from "@aws-sdk/lib-dynamodb";
import { CustomerProfile } from "../utils/validation.js";
import { instrumentDynamo } from "../utils/tracer.js";

const client = instrumentDynamo(new DynamoDBClient({}));
const ddb = DynamoDBDocumentClient.from(client);

export class CrudService {
  private readonly tableName: string = process.env.TABLE_NAME ?? "";

  private pk(id: string): string {
    return `CUSTOMER#${id}`;
  }

  async create(profile: CustomerProfile): Promise<CustomerProfile> {
    const item = {
      pk: this.pk(profile.id),
      sk: "PROFILE",
      gsi1pk: this.pk(profile.id),
      ...profile,
    };
    await ddb.send(new PutCommand({ TableName: this.tableName, Item: item }));
    return profile;
  }

  async get(id: string): Promise<CustomerProfile | null> {
    const res = await ddb.send(
      new GetCommand({
        TableName: this.tableName,
        Key: { pk: this.pk(id), sk: "PROFILE" },
      }),
    );
    return (res.Item as CustomerProfile) ?? null;
  }

  async update(profile: CustomerProfile): Promise<CustomerProfile> {
    await this.create(profile);
    return profile;
  }

  async patch(
    id: string,
    partial: Partial<CustomerProfile>,
  ): Promise<CustomerProfile | null> {
    const updateExp = Object.keys(partial)
      .map((_k, i) => `#k${i} = :v${i}`)
      .join(", ");
    const ExpressionAttributeNames = Object.fromEntries(
      Object.keys(partial).map((k, i) => [`#k${i}`, k]),
    );
    const ExpressionAttributeValues = Object.fromEntries(
      Object.entries(partial).map(([, v], i) => [`:v${i}`, v]),
    );
    const res = await ddb.send(
      new UpdateCommand({
        TableName: this.tableName,
        Key: { pk: this.pk(id), sk: "PROFILE" },
        UpdateExpression: `SET ${updateExp}`,
        ExpressionAttributeNames,
        ExpressionAttributeValues,
        ReturnValues: "ALL_NEW",
      }),
    );
    return res.Attributes as CustomerProfile | null;
  }

  async delete(id: string): Promise<void> {
    await ddb.send(
      new DeleteCommand({
        TableName: this.tableName,
        Key: { pk: this.pk(id), sk: "PROFILE" },
      }),
    );
  }

  async list(): Promise<CustomerProfile[]> {
    const res = await ddb.send(new ScanCommand({ TableName: this.tableName }));
    return (res.Items as CustomerProfile[]) ?? [];
  }
}
```

## File: ./src/utils/logger.ts
```typescript
/**
 * App: Customer API
 * Package: utils
 * File: logger.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Provides a singleton Powertools Logger instance
 *              with environment-aware log level and Lambda context support.
 */

import { Logger } from "@aws-lambda-powertools/logger";

const logger = new Logger({
  serviceName: process.env.POWERTOOLS_SERVICE_NAME ?? "customer-api",
  logLevel: process.env.NODE_ENV === "dev" ? "DEBUG" : "INFO",
});

export default logger;
```

## File: ./src/utils/metrics.ts
```typescript
/**
 * App: Customer API
 * Package: utils
 * File: metrics.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Exposes Powertools Metrics instance and logMetrics decorator
 *              with automatic ColdStart metric emission.
 */

import { Metrics, MetricUnit } from "@aws-lambda-powertools/metrics";
import { logMetrics } from "@aws-lambda-powertools/metrics/middleware";

export const metrics = new Metrics({
  namespace: "CustomerAPI",
  serviceName: process.env.POWERTOOLS_SERVICE_NAME ?? "customer-api",
});

export { MetricUnit, logMetrics };
```

## File: ./src/utils/parser.ts
```typescript
/**
 * App: Customer API
 * Package: utils
 * File: parser.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Helper to parse HTTP API events using Powertools Parser.
 */

import { APIGatewayProxyEventV2 } from "aws-lambda";

export function parseJson<T>(event: APIGatewayProxyEventV2): T {
  if (!event.body) {
    throw new Error("Missing body");
  }
  return JSON.parse(event.body) as T;
}
```

## File: ./src/utils/tracer.ts
```typescript
/**
 * App: Customer API
 * Package: utils
 * File: tracer.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Provides Powertools Tracer singleton and helper to
 *              instrument AWS SDK v3 clients.
 */

import { Tracer } from "@aws-lambda-powertools/tracer";
import { DynamoDBClient } from "@aws-sdk/client-dynamodb";

export const tracer = new Tracer({
  serviceName: process.env.POWERTOOLS_SERVICE_NAME ?? "customer-api",
});

export function instrumentDynamo<T extends DynamoDBClient>(client: T): T {
  return tracer.captureAWSv3Client(client);
}

export default tracer;
```

## File: ./src/utils/validation.ts
```typescript
/**
 * App: Customer API
 * Package: utils
 * File: validation.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:15:51Z
 * Description: Zod schemas representing the CustomerProfile domain model
 *              and helper validation functions.
 */

import { z } from "zod";

export const PhoneNumberSchema = z.object({
  type: z.enum(["mobile", "home", "work", "other"]),
  number: z.string().regex(/^\+?[1-9]\d{1,14}$/),
});

export const PostalAddressSchema = z.object({
  line1: z.string().min(1),
  line2: z.string().optional(),
  city: z.string().min(1),
  state: z.string().min(1),
  postalCode: z.string(),
  country: z.string().min(2).max(2),
});

export const PrivacySettingsSchema = z.object({
  marketingEmailsEnabled: z.boolean(),
  twoFactorEnabled: z.boolean(),
});

export const CustomerProfileSchema = z
  .object({
    id: z.string().uuid(),
    firstName: z.string().min(1),
    middleName: z.string().min(1).optional(),
    lastName: z.string().min(1),
    emails: z
      .array(z.string().email())
      .min(1)
      .refine((arr) => new Set(arr).size === arr.length, {
        message: "emails must be unique",
      }),
    phoneNumbers: z.array(PhoneNumberSchema).min(1).optional(),
    address: PostalAddressSchema.optional(),
    privacySettings: PrivacySettingsSchema,
  })
  .strict();

export type CustomerProfile = z.infer<typeof CustomerProfileSchema>;

export function validateCustomerProfile(data: unknown): CustomerProfile {
  return CustomerProfileSchema.parse(data);
}

export function validatePartialCustomerProfile(
  data: unknown,
): Partial<CustomerProfile> {
  return CustomerProfileSchema.partial().parse(
    data,
  ) as Partial<CustomerProfile>;
}
```

## File: ./test/unit/fixtures/customer.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: fixtures/customer.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Provides sample CustomerProfile objects for unit tests.
 */

import { CustomerProfile } from "../../../src/utils/validation.js";

export const sampleProfile: CustomerProfile = {
  id: "11111111-1111-1111-1111-111111111111",
  firstName: "Alice",
  middleName: "Q",
  lastName: "Doe",
  emails: ["alice@example.com"],
  phoneNumbers: [{ type: "mobile", number: "+1234567890" }],
  address: {
    line1: "123 Main St",
    city: "Metropolis",
    state: "NY",
    postalCode: "12345",
    country: "US",
  },
  privacySettings: {
    marketingEmailsEnabled: true,
    twoFactorEnabled: true,
  },
};
```

## File: ./test/unit/handlers/create.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: create.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the create Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const parseJson = jest.fn();
const validateCustomerProfile = jest.fn();
const create = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/utils/parser.js", () => ({ parseJson }));
jest.unstable_mockModule("../../../src/utils/validation.js", () => ({
  validateCustomerProfile,
}));
jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ create })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/create.js")) as any;

describe("create handler", () => {
  it("creates profile", async () => {
    parseJson.mockReturnValue(sampleProfile);
    validateCustomerProfile.mockReturnValue(sampleProfile);
    create.mockResolvedValueOnce(sampleProfile);
    const event = { body: "{}" } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(create).toHaveBeenCalledWith(sampleProfile);
    expect(res.statusCode).toBe(201);
    expect(JSON.parse(res.body)).toEqual(sampleProfile);
  });
});
```

## File: ./test/unit/handlers/delete.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: delete.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the delete Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const del = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ delete: del })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/delete.js")) as any;

describe("delete handler", () => {
  it("deletes item", async () => {
    del.mockResolvedValueOnce(undefined);
    const event = {
      pathParameters: { id: sampleProfile.id },
    } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(del).toHaveBeenCalledWith(sampleProfile.id);
    expect(res.statusCode).toBe(204);
  });
});
```

## File: ./test/unit/handlers/get.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: get.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the get Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const getItem = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ get: getItem })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/get.js")) as any;

describe("get handler", () => {
  it("returns item when found", async () => {
    getItem.mockResolvedValueOnce(sampleProfile);
    const event = {
      pathParameters: { id: sampleProfile.id },
    } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(res.statusCode).toBe(200);
    expect(JSON.parse(res.body)).toEqual(sampleProfile);
  });

  it("returns 404 when missing", async () => {
    getItem.mockResolvedValueOnce(null);
    const event = {
      pathParameters: { id: sampleProfile.id },
    } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(res.statusCode).toBe(404);
  });
});
```

## File: ./test/unit/handlers/list.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: list.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the list Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const listItems = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ list: listItems })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/list.js")) as any;

describe("list handler", () => {
  it("returns all items", async () => {
    listItems.mockResolvedValueOnce([sampleProfile]);
    const res = await handler(
      {} as unknown as APIGatewayProxyEventV2,
      {} as any,
    );
    expect(res.statusCode).toBe(200);
    expect(JSON.parse(res.body)).toEqual([sampleProfile]);
  });
});
```

## File: ./test/unit/handlers/patch.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: patch.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the patch Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const parseJson = jest.fn();
const validatePartialCustomerProfile = jest.fn();
const patch = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/utils/parser.js", () => ({ parseJson }));
jest.unstable_mockModule("../../../src/utils/validation.js", () => ({
  validatePartialCustomerProfile,
}));
jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ patch })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/patch.js")) as any;

describe("patch handler", () => {
  it("patches profile", async () => {
    parseJson.mockReturnValue({ firstName: "Bob" });
    validatePartialCustomerProfile.mockReturnValue({ firstName: "Bob" });
    patch.mockResolvedValueOnce(sampleProfile);
    const event = {
      body: "{}",
      pathParameters: { id: sampleProfile.id },
    } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(patch).toHaveBeenCalledWith(sampleProfile.id, { firstName: "Bob" });
    expect(res.statusCode).toBe(200);
  });
});
```

## File: ./test/unit/handlers/update.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: update.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the update Lambda handler.
 */

import { jest } from "@jest/globals";
import { APIGatewayProxyEventV2 } from "aws-lambda";
import { sampleProfile } from "../fixtures/customer.js";

const parseJson = jest.fn();
const validateCustomerProfile = jest.fn();
const update = jest.fn() as any;
const addMetric = jest.fn();
const addContext = jest.fn();

jest.unstable_mockModule("../../../src/utils/parser.js", () => ({ parseJson }));
jest.unstable_mockModule("../../../src/utils/validation.js", () => ({
  validateCustomerProfile,
}));
jest.unstable_mockModule("../../../src/services/crud_service.js", () => ({
  CrudService: jest.fn().mockImplementation(() => ({ update })),
}));
jest.unstable_mockModule("../../../src/utils/metrics.js", () => ({
  metrics: { addMetric },
  MetricUnit: { Count: "Count" },
}));
jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  default: { captureLambdaHandler: (h: any) => h },
}));
jest.unstable_mockModule("../../../src/utils/logger.js", () => ({
  default: { addContext },
}));

const { handler } = (await import("../../../src/handlers/update.js")) as any;

describe("update handler", () => {
  it("updates profile", async () => {
    parseJson.mockReturnValue(sampleProfile);
    validateCustomerProfile.mockReturnValue(sampleProfile);
    update.mockResolvedValueOnce(sampleProfile);
    const event = { body: "{}" } as unknown as APIGatewayProxyEventV2;
    const res = await handler(event, {} as any);
    expect(res.statusCode).toBe(200);
    expect(update).toHaveBeenCalledWith(sampleProfile);
  });
});
```

## File: ./test/unit/services/crud_service.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: crud_service.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Unit tests for the CrudService DynamoDB layer.
 */

import { jest } from "@jest/globals";
import { sampleProfile } from "../fixtures/customer.js";

const sendMock = jest.fn() as any;

jest.unstable_mockModule("../../../src/utils/tracer.js", () => ({
  instrumentDynamo: (c: any) => c,
}));

jest.unstable_mockModule("@aws-sdk/lib-dynamodb", () => ({
  DynamoDBDocumentClient: { from: () => ({ send: sendMock }) },
  PutCommand: class {
    constructor(public input: any) {}
  },
  GetCommand: class {
    constructor(public input: any) {}
  },
  UpdateCommand: class {
    constructor(public input: any) {}
  },
  DeleteCommand: class {
    constructor(public input: any) {}
  },
  ScanCommand: class {
    constructor(public input: any) {}
  },
}));

const { CrudService } = (await import(
  "../../../src/services/crud_service.js"
)) as any;

describe("CrudService", () => {
  beforeEach(() => {
    sendMock.mockReset();
  });

  it("creates item", async () => {
    sendMock.mockResolvedValueOnce({});
    const service = new CrudService();
    await service.create(sampleProfile);
    expect((sendMock.mock.calls[0][0] as any).constructor.name).toBe(
      "PutCommand",
    );
  });

  it("gets item", async () => {
    sendMock.mockResolvedValueOnce({ Item: sampleProfile });
    const service = new CrudService();
    const result = await service.get(sampleProfile.id);
    expect(result).toEqual(sampleProfile);
  });

  it("returns null when get misses", async () => {
    sendMock.mockResolvedValueOnce({});
    const service = new CrudService();
    const result = await service.get(sampleProfile.id);
    expect(result).toBeNull();
  });

  it("updates item", async () => {
    sendMock.mockResolvedValueOnce({});
    const service = new CrudService();
    await service.update(sampleProfile);
    expect((sendMock.mock.calls[0][0] as any).constructor.name).toBe(
      "PutCommand",
    );
  });

  it("patches item", async () => {
    sendMock.mockResolvedValueOnce({ Attributes: sampleProfile });
    const service = new CrudService();
    const result = await service.patch(sampleProfile.id, { firstName: "Bob" });
    expect(result).toEqual(sampleProfile);
  });

  it("deletes item", async () => {
    sendMock.mockResolvedValueOnce({});
    const service = new CrudService();
    await service.delete(sampleProfile.id);
    expect((sendMock.mock.calls[0][0] as any).constructor.name).toBe(
      "DeleteCommand",
    );
  });

  it("lists items", async () => {
    sendMock.mockResolvedValueOnce({ Items: [sampleProfile] });
    const service = new CrudService();
    const result = await service.list();
    expect(result).toEqual([sampleProfile]);
  });
});
```

## File: ./test/unit/utils/logger.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: logger.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Ensures logger exports a configured Logger instance.
 */

import { Logger } from "@aws-lambda-powertools/logger";
import logger from "../../../src/utils/logger.js";

describe("logger", () => {
  it("is an instance of Logger", () => {
    expect(logger).toBeInstanceOf(Logger);
  });
});
```

## File: ./test/unit/utils/metrics.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: metrics.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests Metrics utility exports.
 */

import { metrics } from "../../../src/utils/metrics.js";

describe("metrics", () => {
  it("has namespace CustomerAPI", () => {
    // @ts-ignore internal property
    expect(metrics.namespace).toBe("CustomerAPI");
  });
});
```

## File: ./test/unit/utils/parser.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: parser.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests the parseJson utility for correct body parsing.
 */

import { APIGatewayProxyEventV2 } from "aws-lambda";
import { parseJson } from "../../../src/utils/parser.js";

describe("parseJson", () => {
  it("parses JSON body", () => {
    const event = { body: '{"foo":"bar"}' } as APIGatewayProxyEventV2;
    expect(parseJson<{ foo: string }>(event)).toEqual({ foo: "bar" });
  });

  it("throws when body missing", () => {
    const event = { body: undefined } as unknown as APIGatewayProxyEventV2;
    expect(() => parseJson(event)).toThrow("Missing body");
  });
});
```

## File: ./test/unit/utils/tracer.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: tracer.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests instrumentation helper for DynamoDB clients.
 */

import { DynamoDBClient } from "@aws-sdk/client-dynamodb";
import { instrumentDynamo } from "../../../src/utils/tracer.js";

describe("instrumentDynamo", () => {
  it("returns captured client", () => {
    const client = new DynamoDBClient({});
    const captured = instrumentDynamo(client);
    expect(captured).toBe(client);
  });
});
```

## File: ./test/unit/utils/validation.test.ts
```typescript
/**
 * App: Customer API
 * Package: test
 * File: validation.test.ts
 * Version: 0.1.0
 * Author: Codex
 * Date: 2025-06-24T21:41:00Z
 * Description: Tests validation helpers for CustomerProfile domain.
 */

import {
  validateCustomerProfile,
  validatePartialCustomerProfile,
} from "../../../src/utils/validation.js";
import { sampleProfile } from "../fixtures/customer.js";

describe("validation helpers", () => {
  it("validates full profile", () => {
    expect(validateCustomerProfile(sampleProfile)).toEqual(sampleProfile);
  });

  it("validates partial profile", () => {
    const partial = { firstName: "Bob" };
    expect(validatePartialCustomerProfile(partial)).toEqual(partial);
  });

  it("throws on invalid profile", () => {
    expect(() => validateCustomerProfile({})).toThrow();
  });
});
```


# Infrastructure-as-Code (IaC) Report

## File: ./api-gateway-log.sh

```bash
#!/usr/bin/env bash
set -euo pipefail

API_NAME="customerprofile-api-dev"         # <- check spelling in AWS Console
LOG_GROUP="/aws/apigw/${API_NAME}"
REQ_ID="MyNWgieNIAMEM5A="

# macOS-compatible epoch helper
epoch() { date -j -u -f "%Y-%m-%dT%H:%M:%SZ" "$1" +"%s"; }

START=$(epoch "2025-06-26T18:10:00Z")
END=$(epoch   "2025-06-26T18:25:00Z")

echo "Querying $LOG_GROUP from $START to $END for requestId=$REQ_ID"

QUERY_ID=$(aws logs start-query \
  --log-group-name "$LOG_GROUP" \
  --start-time "$START" \
  --end-time   "$END" \
  --query-string "
      fields @timestamp, routeKey, status, error
      | filter requestId = '$REQ_ID'
      | sort @timestamp asc
    " \
  --query "queryId" --output text)

# AWS needs a short wait for the query to finish (~1‒3 s)
sleep 2

aws logs get-query-results --query-id "$QUERY_ID"
```

## File: ./debug.sh

```bash
aws dynamodb get-item \
  --table-name $(terraform output -raw dynamodb_table_name) \
  --key '{
    "pk": {"S":"CUSTOMER#11111111-1111-1111-1111-111101111114"},
    "sk": {"S":"PROFILE"}
  }'
```

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

