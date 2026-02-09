# Installation

`uniget` ships as a statically linked binary and does not require any additional tools to be installed.

## Global context (recommended)

Installation commands for the uniget [CLI](https://gitlab.com/uniget-org/cli).

```bash
curl -sLf https://gitlab.com/uniget-org/cli/-/releases/permalink/latest/downloads/uniget_Linux_$(uname -m).tar.gz \
| sudo tar -xzC /usr/local/bin uniget
```

## User context

Installation commands for the uniget [CLI](https://gitlab.com/uniget-org/cli):

```bash
curl -sLf https://gitlab.com/uniget-org/cli/-/releases/permalink/latest/downloads/uniget_Linux_$(uname -m).tar.gz \
| tar -xzC ~/.local/bin uniget
```

By default `uniget` will operate in global context even if installed inside the home directory. Either use `--user` when running `uniget` or set `$UNIGET_USER`. See [context](context.md) for more information.

## Prerelease versions

Prerelease versions are not published as releases in GitLab.

If you have a working go toolchain installed:

```bash
VERSION=0.25.0-rc.3
go install -ldflags "-s -w -X main.version=${VERSION}" "gitlab.com/uniget-org/cli/cmd/uniget@v${VERSION}"
```

If you have Docker installed:

```bash
VERSION=0.25.0-rc.3
docker run --name=uniget -it golang go install -ldflags "-s -w -X main.version=${Version}" "gitlab.com/uniget-org/cli/cmd/uniget@v${Version}"
docker cp uniget:/go/bin/uniget .
```
