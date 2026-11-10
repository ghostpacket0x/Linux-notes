# Linux Notes

Command line notes from my practice on Kali Linux. Each section has the command, what it does, and an example. Real output is taken from my own VM, with anything sensitive removed.

## Before you start

### Key words

| Word | What it means |
|---|---|
| Terminal | The window where you type commands instead of clicking |
| Command | An instruction you type and run by pressing Enter |
| Directory | Another word for a folder |
| Root | The all-powerful administrator account on Linux. Also the name of the top folder `/` |
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

### Getting help when you are stuck
 
- `<command> --help` shows a short summary, for example `ls --help`.
- `man <command>` opens the full manual, for example `man ls`. Press `q` to leave it.
- `whatis <command>` gives a one-line description.

## Table of contents

1. [Files and navigation](sections/01-files-and-navigation.md)
2. [Viewing and editing text](sections/02-text-and-viewing.md)
3. [Archives and rsync](sections/03-archives-and-rsync.md)
4. [Processes and system information](sections/04-processes-and-system.md)
5. [Disk usage](sections/05-disk-usage.md)
6. [Dates and calendars](sections/06-dates-and-calendars.md)
7. [Networking](sections/07-networking.md)
8. [Users and groups](sections/08-users-and-groups.md)
9. [Packages](sections/09-packages.md)
10. [Services and logs](sections/10-services-and-logs.md)
11. [Terminal multiplexing with tmux](sections/11-tmux.md)
12. [Serving files over HTTP](sections/12-serving-files-over-http.md)
13. [Troubleshooting log](sections/13-troubleshooting-log.md)
14. [Shell builtins and keywords](sections/14-shell-builtins-and-keywords.md)
15. [Printing and other tools](sections/15-printing-and-other-tools.md)

## Practice
 
Practice scenarios go in the [labs](labs/) folder.
