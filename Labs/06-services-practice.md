# Lab 10: Services and logs

**Goal:** read the last few log lines for a service, then check its status.

**Linked section:** [6 Services and logs](../sections/06-services-and-logs.md)

## Steps

```bash
systemctl status ssh
journalctl -u ssh.service -n 10 --no-pager
```

## What to check

If SSH isn't installed, pick another service from `systemctl list-units --type=service` and repeat the steps with its name.

## Part 2: write a service of your own

Create the unit file, load it, and start it:

```bash
sudo nano /etc/systemd/system/lab-hello.service
```

Paste the unit file from section 10, then:

```bash
sudo systemctl daemon-reload
sudo systemctl start lab-hello
systemctl status lab-hello --no-pager
sleep 65
cat /tmp/lab-hello.log
journalctl -u lab-hello --no-pager -n 5
```

### Part 2 checks

- `systemctl status` should show `active (running)`.
- After about 65 seconds, `/tmp/lab-hello.log` should contain at least two dated lines.
- `journalctl -u lab-hello` should show the service starting.

## Clean up

Nothing to clean up.

Remove the service and its log:

```bash
sudo systemctl stop lab-hello
sudo rm /etc/systemd/system/lab-hello.service
sudo systemctl daemon-reload
rm -f /tmp/lab-hello.log
```
