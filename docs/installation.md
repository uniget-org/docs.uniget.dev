# Installation

`uniget` ships as a statically linked binary and does not require any additional tools to be installed.

## Global context (recommended)

Installation commands for the uniget [CLI](https://github.com/uniget-org/cli).

```bash
curl -sLf https://github.com/uniget-org/cli/releases/latest/download/uniget_Linux_$(uname -m).tar.gz \
| sudo tar -xzC /usr/local/bin uniget
```

## User context

Installation commands for the uniget [CLI](https://github.com/uniget-org/cli):

```bash
curl -sLf https://github.com/uniget-org/cli/releases/latest/download/uniget_Linux_$(uname -m).tar.gz \
| tar -xzC ~/.local/bin uniget
```

By default `uniget` will operate in global context even if installed inside the home directory. Either use `--user` when running `uniget` or set `$UNIGET_USER`. See [context](context.md) for more information.
