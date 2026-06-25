# Caching downloads

`uniget` supports caching of downloaded tools. This can be used to improve re-install cycles during testing.

Supported cache backends:

- None (default)
- Filesystem
- Docker
- ContainerD

Selecting a cache backend by...

1. Either set the environment variable `UNIGET_CACHE` to one of `none`, `file`, `docker` or `containerd`
2. Or use the CLI flag `--cache` with one of `none`, `file`, `docker` or `containerd`

Optionally set `UNIGET_CACHE_DIRECTORY` or `--cache-directory` to choose where the file cache is stored. Default is `var/cache/uniget/downloads` in global context and `${XDG_CACHE_HOME:-$HOME/.cache}/uniget/downloads` in user context.

Optionally set `UNIGET_CACHE_RETENTION` or `--cache-retention` to the retention in seconds. Defaults to `86400` (24h).

`uniget` expects that the necessary infrastructure for the selected backend is available:

- `docker`: The Docker daemon must be running and the current user must be able to connect
- `containerd`: The ContainerD daemon must be running and the current user must be able to connect
