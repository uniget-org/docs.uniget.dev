# Hooks

Execute custom scripts before and after installation and uninstallation.

## Types

`uniget`  currently supports four types of hooks:

1. pre-install is executed before any tool is installed and provides a list of tools planned for installation
1. post-install is executed after tools are installed and provides a list of tools actually added
1. pre-uninstall is executed before any tools are uninstalled and provides a list of tools planned for uninstallation
1. post-uninstall is executed after tools are uninstalled and provides a list of tools actually uninstalled

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
    echo $1

    shift
done
```

## Management

If you place scripts in the directories manually, you must make then executable.

You can also use the `hooks` subcommand to manage hooks:

`hook list` displays all hooks of the type specified by the `--type` flag.

`hook add` copies an existing file to the appropriate directory and makes the file executable. The `--type` flag takes the type of hook and the `--source` flag takes the files to copy.

`hook edit` calls your favourite editor to edit a hook. It relies on the environment variable EDITOR which must be seet. The `--type` flag takes the type of hook and exactly one argument naming the hook to edit.

`hook test` is available for testing. The `--type` flag takes the type of hook, one argument naming the hook to run and multiple arguments naming the tools to supply.

`hook run` is available for simulating a specific hook type. The `--type` flag takes the type of hook. All hooks of the specified type are executes.
