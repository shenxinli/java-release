# OpenJDK Build and Release Workflow

This repository contains a GitHub Actions workflow for building and releasing OpenJDK versions. The workflow supports multiple platforms, including Linux (amd64, arm64) and Windows (amd64), and allows you to build JDK versions 11, 17, and 21.

## Workflow Overview

The workflow performs the following tasks:

1. **Checkout code** - Downloads the repository code.
2. **Set up JDK (boot JDK)** - Uses a pre-configured boot JDK for compiling OpenJDK.
3. **Download OpenJDK binaries** - Downloads pre-built OpenJDK binaries from Adoptium for the specified version and platform.
4. **Extract OpenJDK** - Extracts the downloaded OpenJDK binary.
5. **Package OpenJDK** - Packages the extracted OpenJDK as a `.tar.gz` (Linux) or `.zip` (Windows) archive.
6. **Upload Artifact** - Uploads the packaged OpenJDK as an artifact.

The workflow supports the following platforms:
- `linux/amd64`
- `linux/arm64`
- `windows/amd64`

You can select the JDK version (11, 17, or 21) and the platforms for the build.

## Inputs

The workflow allows the following inputs when manually triggered via the GitHub Actions UI:

- **jdk_version**: The version of OpenJDK to build (11, 17, or 21). Default is `17`.
- **platforms**: A comma-separated list of platforms to build for. Default is `linux/amd64, linux/arm64, windows/amd64`.

### Example

To trigger a build for OpenJDK 11 for all platforms, you can trigger the workflow as follows:

```yaml
on:
  workflow_dispatch:
    inputs:
      jdk_version: '11'
      platforms: 'linux/amd64, linux/arm64, windows/amd64'
