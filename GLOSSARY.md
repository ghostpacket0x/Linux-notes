# Glossary

Short definitions of terms used across the notes. Each term links to the section where it's used most.

| Term | Meaning | Where to learn more |
|---|---|---|
| **Alias** | A short name for a longer command, for example `ll` for `ls -l` | [14](sections/14-shell-builtins-and-keywords.md) |
| **Archive** | One file that holds many files, often compressed | [3](sections/03-archives-and-rsync.md) |
| **Cron** | A scheduler that runs commands at set times | [19](sections/19-cron-and-scheduled-tasks.md) |
| **Daemon** | A background program that waits for requests. Often ends in `d`, such as `sshd` | [10](sections/10-services-and-logs.md) |
| **Directory** | Another word for a folder | [1](sections/01-files-and-navigation.md) |
| **Distribution** | A version of Linux with its own packages and tools, such as Kali or Ubuntu | [9](sections/09-packages.md) |
| **Environment variable** | A named value that programs can read, such as `HOME` or `PATH` | [4](sections/04-processes-and-system.md) |
| **Exit code** | A number a command returns when it finishes. `0` means success | [21](sections/21-bash-scripting.md) |
| **Firewall** | Rules that decide which network connections a machine accepts | [20](sections/20-firewall-basics.md) |
| **Glob** | A pattern with `*` or `?` that the shell expands into file names | [2](sections/02-text-and-viewing.md) |
| **Inode** | The record that stores a file's metadata, separate from its name | [1](sections/01-files-and-navigation.md) |
| **Journal** | The log store that `systemd` writes, read with `journalctl` | [17](sections/17-logs-and-monitoring.md) |
| **Kernel** | The core of the operating system that talks to the hardware | [4](sections/04-processes-and-system.md) |
| **Key pair** | A private key you keep and a public key you share, used for SSH login | [18](sections/18-ssh-keys-and-config.md) |
| **Package** | A piece of software installed with a package manager | [9](sections/09-packages.md) |
| **PATH** | The list of folders the shell searches for commands | [1](sections/01-files-and-navigation.md) |
| **PID** | The process ID that Linux gives each running program | [4](sections/04-processes-and-system.md) |
| **Permissions** | The read, write, and execute rights for owner, group, and others | [16](sections/16-permissions-and-ownership.md) |
| **Pipe** | The `\|` symbol that sends one command's output into another | [2](sections/02-text-and-viewing.md) |
| **Port** | A numbered door that a service listens on, such as 22 for SSH | [7](sections/07-networking.md) |
| **Process** | A running program | [4](sections/04-processes-and-system.md) |
| **Redirection** | Sending output to a file with `>` or `>>`, or taking input with `<` | [2](sections/02-text-and-viewing.md) |
| **Root** | The administrator account, and the top folder `/` | [8](sections/08-users-and-groups.md) |
| **Service** | A program that runs in the background, such as SSH | [10](sections/10-services-and-logs.md) |
| **Shebang** | The `#!/bin/bash` line that tells Linux which shell runs a script | [21](sections/21-bash-scripting.md) |
| **Shell** | The program that reads and runs your commands, such as Bash | [14](sections/14-shell-builtins-and-keywords.md) |
| **SGID** | A permission that makes a program run with its group's rights | [22](sections/22-finding-interesting-files.md) |
| **Standard input, output, error** | The three streams a program uses: `stdin`, `stdout`, and `stderr` | [2](sections/02-text-and-viewing.md) |
| **Sticky bit** | A permission on folders like `/tmp` that stops users deleting each other's files | [16](sections/16-permissions-and-ownership.md) |
| **SUID** | A permission that makes a program run with its owner's rights | [22](sections/22-finding-interesting-files.md) |
| **Sudo** | Runs one command with administrator rights | [8](sections/08-users-and-groups.md) |
| **Symbolic link** | A shortcut that points to another file, made with `ln -s` | [1](sections/01-files-and-navigation.md) |
| **systemd** | The service manager that starts and stops services, controlled with `systemctl` | [10](sections/10-services-and-logs.md) |
| **Terminal** | The window where you type commands | [11](sections/11-tmux.md) |
| **tmux session** | A terminal session that keeps running after you close the window | [11](sections/11-tmux.md) |
| **VPN** | A secure tunnel to a private network, such as a Hack The Box lab | [troubleshooting log](sections/13-troubleshooting-log.md) |
| **Wildcard** | Another name for a glob, such as `*.txt` | [2](sections/02-text-and-viewing.md) |
