# Air-gapped installation

`uniget` downloads container images from a publicly available registry. Therefore, an air-gapped installation is currently not possible.

But this can be achieved using the caching feature. Please refer to [caching](caching.md) for more details.

There is no subcommand to warm the cache without installing. The easiest way is to select the cache backend and install the desired tools. By selecting a prefix, the current system will not be polluted.

The Docker based cache backend can be warmed by running the appropriate `docker pull` coommands. But this cache backend requires a running Docker daemon on the target system.

Commands for cache warming:
- Regardless of the cache backend: `uniget --cache=file install TOOL`
- The Docker based cache backend can be warmed out-of-band: `docker pull ghcr.io/uniget-org/tools/TOOL:latest`
- The ContainerD based cache backend can be warmed out-of-band: `ctr image pull ghcr.io/uniget-org/tools/TOOL:latest`
