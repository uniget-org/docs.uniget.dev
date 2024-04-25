# Authoring new tools

This document describes the process for authoring new tools for the uniget installer and updater.

Tools are packaged, stored and transported as container images but containerization is not used to execute the tools. After the installation, tools are available natively. For more details, see [concepts](concepts.md).

1. Fork and clone the [tools repository](https://github.com/uniget-org/tools/pulls)
1. Create a new branch
1. Create a new directory under `tools/` for your tool
1. Instead of beginning from scratch...
    1. Either add files from `@template/` to your new directory
    1. Or copy from an existing tool
1. Refer to [manifest](manifest.md) to customize `manifest.yaml`
1. If the binary for your tool has a different name, use the `binary` field in the `manifest.yaml`. A relative path will be resolved to `${target}/bin`. An absolute path should start with the placeholder `${target}`
1. Mind the following when customizing `Dockerfile.template`
    1. All files must be placed under `/uniget_bootstrap`
    1. The file requires a final target called `prepare`
    1. If you rely on an existing tool to package your tool, declare the respective container image first, e.g. `make`:

        ```
        FROM ghcr.io/uniget-org/tools/make:latest AS make
        ```
    
        If you are using a pinned version instead of the `latest` tag, the tag will not get renovated. This is not recommended.

        The copy the contents into your image:

        ```
        COPY --from=make / /usr/local
        ```

        Also add these dependencies to the `build_dependencies` field in `manifest.yaml`

    1. If you rely on an existing tool to execute your tool (e.g. `go` or `make`), add the dependencies to the `runtime_dependencies` field in `manifest.yaml`
    1. Examples for many scenarios are included in `@template/Dockerfile.template`
1. Build the container image for your new tool: `make TOOL--debug`
    1. Explore the contents interactively
    1. Determine the command to extract the version
    1. Update the `version` field in your `manifest.yaml`. Use the placefolder `${binary}` instead of the binary name
1. Update the Renovate configuration: `make renovate.json`
1. Create a pull request
