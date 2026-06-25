# Subcommands

The following subcommands are available.

## bump

Bump image references in `dockerfile`, `compose`, `kubernetes`, and `gitlab-ci` files. See `uniget bump --help` for details.

## cache

Configure caching of downloaded tools. See [caching](caching.md) for details.

## completion

Generate shell completion scripts

## cron

Install cron jobs for updating the metadata (see `update`) as well as upgrading all tools (see `upgrade`)

See also [cron](cron.md)

## debug (hidden)

Debug parameters

## describe

Show detailed information about a tool.

## env (hidden)

Display installation paths as environment variables. See `uniget env --help` for details.

## generate (hidden)

Generate a `Dockerfile` for a list of tools. See `uniget generate --help` for details.

## healthcheck (hidden)

Check the health of installed tools. See `uniget healthcheck --help` for details.

## help

Display help

## hooks

Execute custom scripts before and after installation and uninstallation. See `uniget hooks --help` for more information. See [hooks](hooks.md).

## import

Start managing existing binaries

## inspect

Show all files belonging to the specified tool: `uniget inspect docker`

## install

Install one or more tools

## list

List available or installed tools

## manpages

Generate manpages for `uniget`

## message

Show messages for a tool

## registry (hidden)

Registry helper commands (`reference`, `index`, `manifest`, `size`, `tags`). See `uniget registry --help` for details.

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

Upgrade all tools

## version

Show the version of an installed tool
