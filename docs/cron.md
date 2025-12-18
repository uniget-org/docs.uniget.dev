# Cron

uniget can be scheduled to run at specific intervals using cron jobs:

```bash
uniget cron create
```

By default, `uniget upgrade --auto-update` will be executed at 0:30 every day and `uniget self-upgrade will be executed at 0:00 every Sunday. Both cron schedules can be customized using the `--upgrade-cron` and `--self-upgrade-cron` flags, respectively.
