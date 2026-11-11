# 17. Logs and monitoring

Logs record what happened on a system: logins, errors, services starting and stopping, and failed attempts. Reading them is one of the fastest ways to troubleshoot a problem.

## Where logs live

Most text logs are in `/var/log`. Many are readable only by root, so use `sudo` when you need them.

| Command | What it does | Example |
|---|---|---|
| `ls /var/log` | Lists the log files | `ls /var/log` |
| `sudo tail -n 20 /var/log/syslog` | Shows the last 20 lines of the general system log | `sudo tail -n 20 /var/log/syslog` |
| `sudo tail -f /var/log/syslog` | Follows the log as new lines arrive. Press `Ctrl+C` to stop | `sudo tail -f /var/log/syslog` |
| `sudo less /var/log/auth.log` | Reads the authentication log (logins and `sudo` use) | `sudo less /var/log/auth.log` |

Not every Kali install writes `syslog` or `auth.log`. If a file is missing, use `journalctl` instead, which is covered below.

## Searching logs

| Command | What it does | Example |
|---|---|---|
| `sudo grep -i "failed" /var/log/auth.log` | Finds failed login lines, ignoring case | `sudo grep -i "failed" /var/log/auth.log` |
| `sudo grep -c "Accepted" /var/log/auth.log` | Counts the successful logins | `sudo grep -c "Accepted" /var/log/auth.log` |
| `sudo zcat /var/log/syslog.2.gz \| grep "error"` | Searches an older, compressed log | `sudo zcat /var/log/syslog.2.gz \| grep "error"` |

## The systemd journal

`journalctl` reads the logs that `systemd` collects. It's often the easiest tool on a modern system.

| Command | What it does | Example |
|---|---|---|
| `journalctl -b` | Shows logs from this boot | `journalctl -b` |
| `journalctl -f` | Follows new journal entries | `journalctl -f` |
| `journalctl -p err -b` | Shows only errors from this boot | `journalctl -p err -b` |
| `journalctl --since "1 hour ago"` | Shows entries from the last hour | `journalctl --since "1 hour ago"` |
| `journalctl -u ssh.service -n 20` | Shows the last 20 lines for one service | `journalctl -u ssh.service -n 20` |

## Writing a test message

`logger` adds a line to the system log, which is useful for practice.

```bash
logger "practice message from my terminal"
journalctl -n 5 --no-pager
```

## Notes

- Read logs with the time in mind. Find the event first, then look at the lines just before and after it.
- Logs can contain usernames and IP addresses. Remove anything private before you share a log in your notes or on GitHub.

## Practice

Try the hands-on lab for this section: [labs/18-logs-practice.md](../labs/18-logs-practice.md)
