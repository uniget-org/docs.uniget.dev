# Hooks

Execute custom scripts before and after installation and uninstallation.

## Types

`uniget`  currently supports four types of hooks:

1. pre-install is executed before any tool is installed and provides a list of tools planned for installation
2. post-install is executed after tools are installed and provides a list of tools actually added
3. pre-uninstall is executed before any tools are uninstalled and provides a list of tools planned for uninstallation
4. post-uninstall is executed after tools are uninstalled and provides a list of tools actually uninstalled

## Directories

Scripts need to be placed in the following directories based on type of hook and [context](context.md):

| Hook           | Global context                       | User context                              |
|----------------|--------------------------------------|-------------------------------------------|
| pre-install    | `/etc/uniget/hooks/pre-install.d`    | `~/.config/uniget/hooks/pre-install.d`    |
| post-install   | `/etc/uniget/hooks/post-install.d`   | `~/.config/uniget/hooks/post-install.d`   |
| pre-uninstall  | `/etc/uniget/hooks/pre-uninstall.d`  | `~/.config/uniget/hooks/pre-uninstall.d`  |
| post-uninstall | `/etc/uniget/hooks/post-uninstall.d` | `~/.config/uniget/hooks/post-uninstall.d` |

## Execution

The list of tools is provided as command line parameters, e.g.

```bash
#!/bin/bash

while test $# -gt 0; do

    # Do whatever you want
    case $1 in
        docker)
            sudo systemctl restart docker.service
            ;;
    esac

    shift
done
```

## Management

If you place scripts in these directories manually, you must make them executable.

You can also use the `hooks` subcommand to manage hooks:

`hooks list` displays all hooks of the type specified by the `--type` flag.

`hooks add` copies an existing file to the appropriate directory and makes the file executable. The `--type` flag takes the hook type and the `--source` flag points to the script to copy.

`hooks edit` opens a hook in your preferred editor. It uses `UNIGET_EDITOR` first and then `EDITOR`. The `--type` flag takes the hook type and exactly one argument naming the hook to edit.

`hooks test` is available for testing. The `--type` flag takes the hook type, one argument naming the hook to run, and one or more arguments naming the tools to supply.

`hooks run` is available for simulating a specific hook type. The `--type` flag takes the hook type. All hooks of the specified type are executed.
