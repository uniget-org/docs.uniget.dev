# Usage

The `uniget` CLI comes with help included. The following scenarios are meant as quickstart tutorials.

## You want the default set of tools

By default, `uniget` will only install a small set of tools.

```bash
uniget install --default
```

### You want to investigate which tools are available

List which tools are available in `uniget`:

```bash
uniget list
```

### You want to install a specific tool

It is possible to install individual tools:

```bash
uniget install gojq
uniget install kubectl helm
```

### You want to search for tools

You can search for the specified term in names, tags and dependencies:

```bash
uniget search jq
```

If you are running this interactively, a small text-based UI offers to install selected tools from the search results.

### You want to update installed tools

Updated tools which are already installed:

```bash
uniget update
uniget upgrade
```

### You want to see what will happen

Show which tools will be processed and updated:

```bash
uniget install containerd --plan
uniget upgrade --plan
```

### Reinstall tool(s)

By adding the `--reinstall` parameter, the selected tools can be reinstalled regardless if they are outdated:

```bash
uniget install gojq --reinstall
```