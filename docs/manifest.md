# Tools

Tools are located under the `tools/` subdirectory. Each tool directory must have `manifest.yaml` and `Dockerfile.template`.

Template files are located in `@template/`.

## `manifest.yaml`

The manifest file contains all information about a tool except for the installation instructions. The schema is available at https://uniget.dev/schema.yaml - the source is located here https://gitlab.com/uniget-org/tools.uniget.dev/-/blob/main/site/static/schema.yaml?ref_type=heads.

```yaml
# yaml-language-server: $schema=https://uniget.dev/schema.yaml
$schema: https://uniget.dev/schema.yaml
name: foo
version: "1.2.3"
binary: fooctl
check: ${binary} --version | cut -d' ' -f3 | tr -d v
build_dependencies:
- bar
runtime_dependencies:
- baz
platforms:
- linux/amd64
- linux/arm64
tags:
- docker
- oci
homepage: https://github.com/foo/foo
description: More foo than bar
renovate:
  datasource: github-releases
  package: foo/foo
  extractVersion: ^v(?<version>.+?)$
  allowPrereleases: false
```

The following fields are mandatory for `uniget` to operate:

- `name` - The name must be unique and must match the name of the subdirectory under `tools/`.

- `version` - Version contains the version string without any prefixes or suffixes.

The following fields are strongly recommended for additional value:

- `tags` - Every tool should have a list of tags. Tags offer a different approach of installing tools by specifying a topics to install multiple tools at once.

- `homepage` - The homepage points to a site with more information about the tool, e.g. project homepage.

- `repository`- The repository points to the source code repository of the tool, e.g. GitHub repository.

- `description` - The description contains a short summary what the tool does, e.g. the description from the GitHub project page.

Optional fields:

- `binary` defaults to `${name}` and will be interpreted relative to `${target}/bin/`. `binary` can also be set to the string `"false"` if the tool does not contain a binary, e.g. only configuration files.

- `check` is optional and may contain a command or pipe to extract the version of the installed tool. If `check is empty`, `uniget` default to using a marker file located at `${uniget_cache}/<name>/<version>`.

- `build_dependencies` and `runtime_dependencies` are lists of dependent tools. Build dependencies are installed before a new version is packaged and runtime dependencies are automatically installed with the tool.

- `platforms` - This contains the platforms supported for the tool. If empty or missing, a value of `["linux/amd64"]` is assumed. Only `linux/amd64` and `linux/arm64` are supported.

- `renovate` - The fields are used to generate one [regex manager](https://docs.renovatebot.com/modules/manager/regex/) per tool. If `allowPrerelease` is specified, a [package rule](https://docs.renovatebot.com/configuration-options/#packagerules) is generated per tool as well.

    - `datasource` contains the name of the [datasource](https://docs.renovatebot.com/modules/datasource/), e.g. `github-releaes` and maps to [datasourceTemplate](https://docs.renovatebot.com/configuration-options/#datasourcetemplate)
    - `package` contains the name of the dependency under the specified datasource and maps to [depNameTemplate](https://docs.renovatebot.com/configuration-options/#depnametemplate)
    - `extractVersion` defines how to extract the version from maps to [extractVersionTemplate](https://docs.renovatebot.com/configuration-options/#extractversiontemplate)
    - `allowPrerelease` maps to [ignoreUnstable](https://docs.renovatebot.com/configuration-options/#ignoreunstable)

## `Dockerfile.template`

The `Dockerfile.template` file is used to create the `Dockerfile`. The `Dockerfile.template` must define a target called `prepare` which contains a subdirectory called `uniget_bootstrap`. The contents of this directory will be copied to the final image.

## Reference of variables

The following variables are available in `Dockerfile.template`:

- `arch` - system architecture (`x86_64` or `aarch64`)
- `alt_arch` - alternative name for system architecture (`amd64` or `arm64`)
- `prefix` - used to install into a subdirectory (empty by default)
