# Subcommands

The following subcommands are available.

## bump

Bump image references for a tool to the latest version. Supports `dockerfile`, `compose` and `kubernetes`. See `uniget bump --help` for details.

## cache

Configure caching of downloaded tools. See [caching](caching.md) for details.

## completion

Generate completion scripts

## cron

Install cron jobs for updating the metadata (see `update`) as well as upgrading all tools (see `upgrade`)

See also [cron](cron.md)

## describe

Show detailed information about a tool.

## generate (hidden)

Generate a `Dockerfile` for a list of tools. See `uniget generate --help` for details.

## healthcheck (hidden)

Check the health of installed tools. See `uniget healthcheck --help` for details.

## help

Display help

## hooks (hidden, upcoming)

Execute custom scripts before and after installation and uninstallation. See `uniget hooks --help` for more information.

## inspect

Show all files belonging to the specified tool: `uniget inspect docker`

## install

Install one or more tools

## list

List available or installed tools

## man

Install manpages for uniget

## message

Show messages for a tools

## release-notes

Show release notes for a tool

## search

Search for tools

## self-upgrade

Upgrade uniget to the latest version

## shim

Install shim(s)

## tags

Show tags used for available tools

## uninstall

Remove one or more tools

## update

Update metadata about tools

See also [concepts](concepts.md)

## upgrade

Upgrade a tool to the latest version

## version

Show the version of an installed tool
