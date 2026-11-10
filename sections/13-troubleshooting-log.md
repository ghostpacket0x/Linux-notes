# 13. Troubleshooting log

Real problems I hit while practising, why they happened, and how I fixed them. Fixing errors is the best way to learn.

## Problems

| Problem | Why it happens | Fix |
|---|---|---|
| `Failed to fetch ... 404 Not Found` during apt | The package list is out of date, so apt looks for files that no longer exist | `sudo apt clean`, then `sudo apt update`, then `sudo apt full-upgrade -y` |
| `Could not open lock file ... Permission denied` | apt needs administrator rights and was run without them | Add `sudo`: `sudo apt update` |
| `npx: command not found` | npm is not installed | `sudo apt install npm` |
| `Error opening configuration file` for `.ovpn` | The file is not in the folder given | Find it with `find ~ -name "1.ovpn"`, then use the full path |
| `cannot open display:` for a GUI app | The app was started from a terminal that has no desktop connection | Launch it from the desktop menu |
| `unknown cmd` in tmux | A normal shell command was typed at the tmux prompt | Use `Ctrl+b` then `:` for tmux commands only |
| aptitude proposed removing 32 packages | A dependency conflict: it wanted to remove software to make the upgrade work | Rejected the plan and used `apt full-upgrade` instead |
| `su -` authentication failure | Root has no password set on Kali | Use `sudo` instead |
| Leftover `/home/<name>` folder | The account was deleted without its home folder | Backed it up, checked the contents, then removed it |
| `deluser` backup archive was empty | The account did not exist | Confirmed with `id`, `getent`, and `ls /home` |

## Shell builtins to check with `help`

These are part of the shell, so they're listed here rather than in a section:

`alias` / `unalias`, `enable`, `exec`, `exit`, `export`, `eval`, `dirs`, `pushd`, `popd`, `for`, `if`, `select`, `until`, `while`, `hash`, `help`, `history`, `let`, `local`, `return`, `set`, `shift`, `shopt`, `source`, `test`, `type`, `ulimit`, `umask`, `unset`

## Less common commands to verify

Some entries are printing or niche tools that may not be installed on Kali by default. Check each one before adding it to your notes:

| Command | What it is | Package |
|---|---|---|
| `lpc` | Line printer control (legacy) | `cups-client` or `lpr` |
| `lpr` | Submit a file to the print queue | `cups-client` or `lpr` |
| `lp` | Submit a file to the print queue (CUPS) | `cups-client` |
| `lpstat` | Shows printer and job status (CUPS) | `cups-client` |
| `cancel` | Cancels a print job (CUPS) | `cups-client` |
| `lprm` | Removes a job from the print queue (legacy) | `lpr` |
| `remsync` | Synchronises files between local and remote | `bsdutils` (not default) |
| `mkisofs` | Creates an ISO 9660 image (now `genisoimage` or `xorriso`) | `genisoimage` |
| `notify-send` | Sends a desktop notification | `libnotify-bin` |
| `xdg-open` | Opens a file with the default application | `xdg-utils` |
| `expect` | Automates interactive programs | `expect` (not default) |
| `gawk` | GNU awk (text processing) | `gawk` (usually pre-installed) |
| `getopts` | Bash builtin for parsing script options | built-in |

> `env`, `printenv`, and `fuser` are covered in section 04.   
