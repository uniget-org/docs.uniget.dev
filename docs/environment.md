# Environment variables

The [global parameters](global-parameters.md) can be configured using environment variables.

## Logging

Increase verbosity of output:

- `$UNIGET_LOG_LEVEL`
- `$UNIGET_DEBUG`
- `$UNIGET_TRACE`

## Directories

Set the base directory using `$UNIGET_PREFIX` or `--prefix`. See [chroot](chroot.md) for more information.

Set the target directory `$UNIGET_TARGET` or `--target`.

Set the user context using `$UNIGET_USER` or `--user`. See [context](context.md) for more information.

## User interaction

Disable user interaction with `$UNIGET_NO_INTERACTIVE=1` or `--no-interactive`.