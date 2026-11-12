# 19. Cron and scheduled tasks

Cron runs commands at set times, such as a backup every night or a check every five minutes. Each user has a crontab, and the system has its own schedules.

## Editing and viewing a crontab

| Command | What it does | Example |
|---|---|---|
| `crontab -e` | Opens your crontab in an editor | `crontab -e` |
| `crontab -l` | Lists your scheduled jobs | `crontab -l` |
| `crontab -r` | Deletes **all** your jobs. Use with care | `crontab -r` |

## The five time fields

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── day of the week (0 to 7, where 0 and 7 are Sunday)
│ │ │ └──── month (1 to 12)
│ │ └────── day of the month (1 to 31)
│ └──────── hour (0 to 23)
└────────── minute (0 to 59)
```

| Schedule | Meaning |
|---|---|
| `*/5 * * * *` | Every 5 minutes |
| `0 2 * * *` | Every day at 02:00 |
| `30 8 * * 1` | Every Monday at 08:30 |
| `0 0 1 * *` | At midnight on the first day of each month |

## Recording the output

Cron doesn't show output on screen, so send it to a log file:

```
*/5 * * * * date >> ~/cron-test.log 2>&1
```

`>>` appends to the file, and `2>&1` also captures any errors.

## Other scheduled jobs

| Command | What it does | Example |
|---|---|---|
| `ls /etc/cron.d/` | Lists extra system cron files | `ls /etc/cron.d/` |
| `cat /etc/crontab` | Shows the system crontab | `cat /etc/crontab` |
| `systemctl list-timers` | Shows systemd timers and when each runs next | `systemctl list-timers` |

## Notes

- A job that works in your terminal may fail in cron, because cron has fewer environment variables. Use full paths, for example `/usr/bin/date`.
- Check `~/cron-test.log` after a few minutes to confirm the job ran.

## Practice

Try the hands-on lab for this section: [Labs/19-cron-practice.md](../Labs/19-cron-practice.md)
