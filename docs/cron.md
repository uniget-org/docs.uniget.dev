# Cron

uniget can be scheduled to run at specific intervals using cron jobs:

```bash
uniget cron create
```

By default, `uniget upgrade --auto-update` is executed at `30 0 * * *` (daily at 00:30), and `uniget self-upgrade` is executed at `0 0 * * *` (daily at 00:00). Both schedules can be customized using `--upgrade-cron` and `--self-upgrade-cron`.
