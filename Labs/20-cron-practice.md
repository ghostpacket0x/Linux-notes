# Lab 20: Cron and scheduled tasks

**Goal:** schedule a small job, confirm it runs, then remove it.

**Linked section:** [19 Cron and scheduled tasks](../sections/19-cron-and-scheduled-tasks.md)

## Steps

Open your crontab and add a job that runs every minute:

```bash
crontab -e
```

Add this line, save, and exit:

```
* * * * * date >> ~/cron-test.log 2>&1
```

Wait two minutes, then check:

```bash
crontab -l
cat ~/cron-test.log
systemctl list-timers --no-pager | head -5
```

## What to check

`cron-test.log` should contain at least two dated lines.

## Clean up

Run `crontab -e`, delete the line you added, save, and exit. Then remove the log:

```bash
rm ~/cron-test.log
```

Don't use `crontab -r` for this lab, because it deletes every job in your crontab.
