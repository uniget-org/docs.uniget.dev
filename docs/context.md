# Context

`uniget` was primarily written to install tools with root permissions. Since version [0.11.0-beta.1](https://github.com/uniget-org/cli/releases/tag/v0.11.0-beta.1) to install in user context.

## Global context

Installation in global context requires root permissions or `sudo` to work. This will install the tools in the following directories:

- `/usr/local` for tools
- `/var/lib/uniget` for state
- `/var/cache/uniget` for cached data

You can modify these directories with the `--target`, `--lib-root` and `--cache-root` flags.

### Example

Create a dedicated directory for `uniget`:

```bash
sudo uniget --target=/opt/uniget install gojq
```

## User context

If root permissions are not available or not desired, add the `--user` flag to install in user context. Alternatively, set the UNIGET_USER environment variable, for example with `export UNIGET_USER=1`
This will install the tools in the user's home directory using the following paths:

- `~/.local` for tools
- `~/.local/var/lib/uniget` for state
- `~/.cache/uniget` for cached data

Please make sure that `~/.local/bin` (and similar) is in your `PATH` environment variable.

You cannot use `--prefix` or `--target` in user context.

### Example

Install tools inside your home directory:

```bash
uniget --user install gojq

# alternative:
export UNIGET_USER=1
uniget install gojq
```
