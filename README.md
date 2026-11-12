# Linux Notes

Command line notes from my practice on Kali Linux. Each section has the command, what it does, and an example. Real output is taken from my own VM, with anything sensitive removed.

> **Tested on:** Kali Linux (rolling release). Check your version with `cat /etc/os-release`. Package names and output can change between versions.

## Start here

New to Linux? Read sections 1 and 2 first, then try the practice task at the end of each section. Work through the sections in order, and use the [Labs](Labs/) folder for longer scenarios.

## Before you start 

### Key words

| Word | What it means |
|---|---|
| Terminal | The window where you type commands instead of clicking |
| Command | An instruction you type and run by pressing Enter |
| Directory | Another word for a folder |
| Root | The all-powerful administrator account on Linux. Also the name of the top-level directory `/` |
| `sudo` | Runs one command with administrator rights. Linux asks for your password |
| PID | Process ID, the number Linux gives every running program |
| Package | A piece of software you install with a package manager |
| Service | A program that runs in the background and waits for requests, like SSH |
| Port | A numbered door on a computer that a service listens on, like 22 for SSH |

### How to read the examples

- Anything in `<angle brackets>` is a placeholder. Replace it with your own value. For example, `<name>` could become `alex`.
- The `|` symbol is called a pipe. It sends the output of one command into the next one.
- Linux is case-sensitive: `Notes.txt` and `notes.txt` are different files.
- Press the **Tab** key while typing a name and Linux will try to finish it for you.
- Press **Ctrl+C** to stop a command that is running.

## Getting Help When You're Stuck

### Understanding Commands :

- **`command --help`** shows a short summary. Example: `ls --help`.
- **`man command`** opens the full manual. Example: `man ls`. Press **q** to leave it.
- **`whatis command`** gives a one-line description. Example: `whatis ls`.

### Locating Commands :

- **`which command`** prints the full path of the executable in `$PATH`. Example: `which ls` → `/usr/bin/ls`.
- **`whereis command`** locates the binary, source, and man page in one go. Example: `whereis ls` → `/usr/bin/ls /usr/share/man/man1/ls.1.gz`.

> **`which` vs `whereis`:** `which` only finds executables and searches `$PATH`. `whereis` searches fixed system directories and can locate binaries, sources, and man pages simultaneously.

## Table of contents

1. [Files and navigation](sections/01-files-and-navigation.md)
2. [Viewing and editing text](sections/02-text-and-viewing.md)
3. [Users and groups](sections/03-users-and-groups.md)
4. [Packages](sections/04-packages.md)
5. [Processes and system information](sections/05-processes-and-system.md)
6. [Services and logs](sections/06-services-and-logs.md)
7. [Archives and rsync](sections/07-archives-and-rsync.md)
8. [Disk usage](sections/08-disk-usage.md)
9. [Dates and calendars](sections/09-dates-and-calendars.md)
10. [Networking](sections/10-networking.md)
11. [Terminal multiplexing with tmux](sections/11-tmux.md)
12. [Serving files over HTTP](sections/12-serving-files-over-http.md)
13. [Troubleshooting log](sections/13-troubleshooting-log.md)
14. [Shell builtins and keywords](sections/14-shell-builtins-and-keywords.md)
15. [Printing and other tools](sections/15-printing-and-other-tools.md)
16. [Permissions and ownership](sections/16-permissions-and-ownership.md)
17. [Logs and monitoring](sections/17-logs-and-monitoring.md)
18. [SSH keys and configuration](sections/18-ssh-keys-and-config.md)
19. [Cron and scheduled tasks](sections/19-cron-and-scheduled-tasks.md)
20. [Firewall basics](sections/20-firewall-basics.md)
21. [Bash scripting basics](sections/21-bash-scripting.md)
22. [Finding interesting files](sections/22-finding-interesting-files.md)

## Glossary and contributing

- [Glossary](GLOSSARY.md): short definitions of the terms used across the notes
- [Contributing](CONTRIBUTING.md): how to report problems and suggest changes

## Practice

Practice scenarios go in the [Labs](Labs/) folder. Each section also ends with a short practice task that uses its commands.
