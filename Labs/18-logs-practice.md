# Lab 18: Logs and monitoring

**Goal:** write a test message to the system log, then find it with `journalctl` and `grep`.

**Linked section:** [17 Logs and monitoring](../sections/17-logs-and-monitoring.md)

## Steps

```bash
logger "lab18 test message"
journalctl -n 5 --no-pager
journalctl --since "10 minutes ago" | grep "lab18"
sudo grep "lab18" /var/log/syslog
```

Then follow the journal while you do something else in another terminal:

```bash
journalctl -f
```

Press `Ctrl+C` to stop it.

## What to check

- The `journalctl` search should show your `lab18 test message` line.
- If `/var/log/syslog` doesn't exist, skip the last command. The journal result is enough.

## Clean up

Nothing to clean up. The test message will age out of the log on its own.
