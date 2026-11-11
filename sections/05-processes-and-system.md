# 5. Processes and system information

## Quick reference

| Command | What it does |
|---|---|
| `ps` | Shows process status |
| `pstree` | Tree view of parent/child processes |
| `top` | Live view of running processes |
| `htop` | Friendlier, interactive version of `top` |
| `jobs` **(builtin)** | Lists jobs in this terminal |
| `kill` | Sends a signal to a process, e.g. `kill -9 <PID>` |
| `killall` | Stops processes by name |
| `pkill` | Stops processes that match a pattern |
| `bg` **(builtin)** | Resumes a paused job in the background |
| `fg` **(builtin)** | Brings a job to the foreground |
| `watch` | Runs a command repeatedly and shows the output |
| `killall` | Stops every process with that name |
| `pkill` | Stops processes whose name matches a pattern |
| `nice` | Starts a command with a set priority |
| `renice` | Changes the priority of a running process |
| `nohup` | Runs a command so it keeps going after you log out |
| `lsof` | Lists open files and which process uses them |
| `fuser` | Shows which process uses a file or port |
| `strace` | Traces the system calls a program makes |
| `suspend` **(builtin)** | Pauses the current shell |
| `sleep` | Waits for a set time |
| `time` | Measures how long a command takes |
| `times` **(builtin)** | Shows user and system CPU time for the shell |
| `trap` **(builtin)** | Runs a command when a signal arrives |
| `wait` **(builtin)** | Waits for background jobs to finish |
| `uptime` | Shows how long the system has been running |
| `hostname` | Prints or sets the system name |
| `dmesg` | Shows kernel messages |
| `vmstat` | Reports virtual memory statistics |
| `tty` | Prints the name of the current terminal |
| `env` | Shows environment variables |
| `printenv` | Prints the value of one environment variable |
| `free` | Shows memory (RAM) and swap usage |
| `uname` | Prints system information |
| `id` | Shows your user ID and groups |
| `who` | Shows who is logged in |
| `w` | Shows who is logged in and what they are doing |
| `lsblk` | Lists disks and partitions |
| `lsusb` | Lists USB devices |
| `lscpu` | Shows details about the processor |
| `lspci` | Lists internal devices like graphics and network cards |

## Processes

A **process** is a running program. These commands show what is running and what your machine is made of.

| Command | What it does | Example |
|---|---|---|
| `ps` | Lists processes in your current terminal | `ps` |
| `ps aux` | Lists every process from every user | `ps aux` |
| `ps auxf` | Same list, drawn as a tree of parent and child processes | `ps auxf` |
| `pstree -p` | A tree view with each PID | `pstree -p` |
| `ps -p <PID> -o <columns>` | Shows chosen details about one process | `ps -p 1 -o pid,user,cmd` |
| `ps aux \| grep bash` | Finds processes whose line contains "bash" | `ps aux \| grep bash` |
| `top` | A live view of running processes. Press `q` to quit | `top` |
| `htop` | A friendlier version of `top` (you may need to install it) | `htop` |
| `jobs` | Lists programs running in the background of this terminal | `jobs` |
| `kill <PID>` | Asks a process to stop | `kill 1234` |
| `kill -9 <PID>` | Force-stops a process that ignores a normal `kill`. Use it as a last resort, because the process gets no chance to clean up | `kill -9 1234` |
| `kill -l` | Lists the signals that `kill` can send | `kill -l` |
| `bg` | Resumes a paused job in the background | `bg` |
| `fg <number>` | Brings a background or paused job back to the front. The number comes from `jobs` | `fg 1` |
| `watch -n <seconds> <command>` | Repeats a command on a timer | `watch -n 5 free -h` |

### Job control in practice

1. Start a program, then press `Ctrl+Z` to pause it.
2. Type `jobs` to see your jobs and their numbers.
3. Type `bg` to let the paused job carry on in the background, or `fg 1` to bring job number 1 back to the front.

## More process commands

| Command | What it does | Example |
|---|---|---|
| `killall <name>` | Stops every process with that name | `killall firefox` |
| `pkill <pattern>` | Stops processes whose name matches a pattern | `pkill sleep` |
| `nice -n 10 <command>` | Starts a command with a lower priority | `nice -n 10 gzip big.txt` |
| `renice -n 5 -p <PID>` | Changes the priority of a running process | `renice -n 5 -p 1234` |
| `nohup <command> &` | Keeps a command running after you log out | `nohup ./long.sh &` |
| `lsof` | Lists open files and which process uses them | `sudo lsof -i :8080` |
| `fuser <file or port>` | Shows which process uses a file or port | `sudo fuser -v 8080/tcp` |
| `strace <command>` | Shows the system calls a program makes | `strace ls` |
| `suspend` | Pauses the current shell (shell builtin) | `suspend` |
| `sleep <seconds>` | Waits for a set time | `sleep 10` |
| `time <command>` | Measures how long a command takes | `time ls` |
| `times` | Shows the CPU time used by the shell (shell builtin) | `times` |
| `trap` | Runs a command when a signal arrives (shell builtin) | `trap "echo bye" EXIT` |
| `wait` | Waits for background jobs to finish (shell builtin) | `wait` |
| `uptime` | Shows how long the system has been running | `uptime` |
| `hostname` | Prints or sets the system name | `hostname` |
| `dmesg` | Shows kernel messages (use `sudo` on some systems) | `sudo dmesg \| tail` |
| `vmstat` | Reports virtual memory statistics | `vmstat 2 5` |
| `tty` | Prints the name of the current terminal | `tty` |
| `env` | Shows environment variables, or runs a command with changed ones | `env \| grep HOME` |
| `printenv <name>` | Prints the value of one environment variable | `printenv HOME` |

## Memory and system details

| Command | What it does | Example |
|---|---|---|
| `free` | Shows memory (RAM) and swap usage | `free` |
| `free -m` / `-g` / `-h` | Shows it in megabytes, gigabytes, or an easy-to-read form | `free -h` |
| `uname` | Shows the operating system name | `uname` |
| `uname -a` | Shows kernel version and system details | `uname -a` |
| `id` | Shows who you are: your user ID and groups | `id` |
| `who` | Shows who is logged in | `who` |
| `w` | Shows who is logged in and what they are doing | `w` |

## Hardware

| Command | What it does | Example |
|---|---|---|
| `lsblk` | Lists disks and partitions | `lsblk` |
| `lsusb` | Lists USB devices | `lsusb` |
| `lscpu` | Shows details about the processor | `lscpu` |
| `lspci` | Lists internal devices like graphics and network cards | `lspci` |   
