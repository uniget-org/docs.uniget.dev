# Global Parameters

The following global parameters are available for all commands. See also [environment](environment.md)

## `--help`

Show help on the console.

## `--version`

Show version of `uniget` on the console.

## `--prefix`

Base directory for the installation (useful when preparing a chroot environment). See also [chroot](chroot.md)

## `--target`

Target directory for installation relative to PREFIX (default "usr/local")

## `--user`

Install in user context. See also [context](context.md)

## `--log-level`

Log level (trace, debug, info, warning, error) (default "warning")

## `--debug`

Sets debug log level. Short for `--log-level=debug`.

## `--trace`

Sets trace log level. Short for `--log-level=trace`.

## `--no-interactive`

Disables interactive menus and prompts. This feature was removed in 0.12.0.
