# 6. Services and logs

A **service** is a program that runs quietly in the background and waits for requests, such as SSH (remote login). Linux manages services with `systemctl`, and records what happens in logs you can read with `journalctl`.

| Command | What it does | Example |
|---|---|---|
| `systemctl status ssh` | Shows whether the SSH service is running | `systemctl status ssh` |
| `sudo systemctl start ssh` | Starts the service now | `sudo systemctl start ssh` |
| `sudo systemctl stop ssh` | Stops the service now | `sudo systemctl stop ssh` |
| `sudo systemctl enable ssh` | Makes it start automatically every time the machine boots | `sudo systemctl enable ssh` |
| `sudo systemctl disable ssh` | Stops it starting automatically at boot | `sudo systemctl disable ssh` |
| `journalctl` | Shows the system logs | `journalctl` |
| `journalctl -u <service>` | Shows the logs for one service only | `journalctl -u ssh.service` |
| `reboot` | Restarts the system | `sudo reboot` |
| `shutdown -h now` | Shuts down the system now | `sudo shutdown -h now` |

> Only run an SSH service on machines you own, and turn it off when you don't need it. A running service is a door that others can try to open.

## Writing your own service

A service is described by a **unit file**. Unit files live in `/etc/systemd/system/` and end in `.service`.

```ini
[Unit]
Description=Lab hello service
After=network.target

[Service]
Type=simple
ExecStart=/bin/sh -c 'while true; do date >> /tmp/lab-hello.log; sleep 60; done'
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

| Section | What it controls |
|---|---|
| `[Unit]` | A description, and what must start first (`After=`) |
| `[Service]` | The command to run (`ExecStart=`), how to restart it (`Restart=`), and which user runs it (`User=`) |
| `[Install]` | Which target starts it at boot (`WantedBy=`). `multi-user.target` is the normal non-graphical boot target |

Rules that cause most mistakes:

- `ExecStart=` needs the full path to the program, such as `/bin/sh`, not just `sh`.
- Run `sudo systemctl daemon-reload` after every change to a unit file, so systemd reads it.
- `systemctl enable` makes the service start at boot, and `systemctl disable` removes that.
- Only install a service you understand. A service that runs at boot is a permanent process on your machine.

## Practice

Try the hands-on lab for this section: [Labs/06-services-practice.md](../Labs/06-services-practice.md)
