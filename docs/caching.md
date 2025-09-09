# Caching downloads

`uniget` supports caching of downloaded tools. This can be used to improve re-install cycles during testing.

Supported cache backends:
- None (default)
- Filesystem
- Docker
- ContainerD

Selecting a cache backend by...
1. Either set the environment variable `UNIGET_CACHE` to one of `none`, `file`, `docker` or `containerd`
1. Or use the CLI flag `--cache` with one of `none`, `file`, `docker` or `containerd`

Optionally set `UNIGET_CACHE_DIR` or `--cache-directory` to a directory to store the cache (default: `${XDG_CACHE_HOME:-$HOME/.cache}/uniget`).

Optionally set `UNIGET_CACHE_RETENTION` or `--cache-retention` to a duration string (e.g. `72h`) to invalidate old cache entries. Defaults to 24h.

`uniget` expects that the necessary infrastructure for the selected backend is available:
- `docker`: The Docker daemon must be running and the current user must be able to connect
- `containerd`: The ContainerD daemon must be running and the current user must be able to connect
