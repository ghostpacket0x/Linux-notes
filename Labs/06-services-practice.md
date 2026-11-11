# Lab 06: Services and logs

**Goal:** read the last few log lines for a service, then check its status.

**Linked section:** [06-services-and-logs](../sections/06-services-and-logs.md)

## Steps

```bash
systemctl status ssh
journalctl -u ssh.service -n 10 --no-pager
```

## What to check

If SSH isn't installed, pick another service from `systemctl list-units --type=service` and repeat the steps with its name.

## Clean up

Nothing to clean up.
