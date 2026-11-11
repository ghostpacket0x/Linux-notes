# 6. Services and logs

A **service** is a program that runs quietly in the background and waits for requests, such as SSH (remote login). Linux manages services with `systemctl`, and records what happens in logs you can read with `journalctl`.

## Quick reference

| Command | What it does |
|---|---|
| `systemctl status` | Shows whether a service is running |
| `systemctl start` | Starts a service now |
| `systemctl stop` | Stops a service now |
| `systemctl enable` | Makes a service start at boot |
| `systemctl disable` | Stops a service from starting at boot |
| `journalctl` | Shows the system logs |
| `journalctl -u` | Shows logs for one service only |
| `reboot` | Restarts the system |
| `shutdown` | Shuts down or restarts the system |
| `dmesg` | Kernel messages (see section 04) |

## Managing services with systemctl

| Command | What it does | Example |
|---|---|---|
| `systemctl status ssh` | Shows whether the SSH service is running | `systemctl status ssh` |
| `sudo systemctl start ssh` | Starts the service now | `sudo systemctl start ssh` |
| `sudo systemctl stop ssh` | Stops the service now | `sudo systemctl stop ssh` |
| `sudo systemctl enable ssh` | Makes it start automatically every time the machine boots | `sudo systemctl enable ssh` |
| `sudo systemctl disable ssh` | Stops it starting automatically at boot | `sudo systemctl disable ssh` |

## Reading logs with journalctl

| Command | What it does | Example |
|---|---|---|
| `journalctl` | Shows the system logs | `journalctl` |
| `journalctl -u <service>` | Shows the logs for one service only | `journalctl -u ssh.service` |

## Restarting and shutting down

| Command | What it does | Example |
|---|---|---|
| `reboot` | Restarts the system | `sudo reboot` |
| `shutdown -h now` | Shuts down the system now | `sudo shutdown -h now` |

> Only run an SSH service on machines you own, and turn it off when you don't need it. A running service is a door that others can try to open.   

## Practice 

Try the hands-on lab for this section: [Labs/06-services-practice.md](../Labs/06-services-practice.md)
