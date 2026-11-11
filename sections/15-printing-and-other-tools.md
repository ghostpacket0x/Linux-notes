# 15. Printing and other tools

These tools were listed in reference screenshots but don't fit neatly into one of the earlier sections. Printing tools need a printer and the CUPS printing system, so on a VM without one they usually report that no printer is set up.

## Printing

| Command | What it does | Example |
|---|---|---|
| `lpr <file>` | Sends a file to the printer | `lpr notes.txt` |
| `lprint <file>` | Prints a file | `lprint notes.txt` |
| `lpc` | Controls the printer queue | `lpc status` |
| `lpq` | Lists the print queue | `lpq` |
| `lprintq` | Lists the print queue | `lprintq` |
| `lprm <job>` | Removes jobs from the print queue | `lprm 1` |
| `lprintd` | Cancels a print job | `lprintd` |
| `printcap` | Printer configuration database | `cat /etc/printcap` |

## Other tools

| Command | What it does | Example |
|---|---|---|
| `mkisofs` | Creates an ISO disk image from files | `mkisofs -o disk.iso folder/` |
| `notify-send` | Sends a desktop notification | `notify-send "Done" "Backup finished"` |
| `xdg-open <file or URL>` | Opens a file or URL in its default application | `xdg-open https://example.com` |
| `remsync` | Syncs remote files by email (niche, check before use) | `remsync` |
| `expect` | Automates programs that need interactive input (install with `sudo apt install expect`) | `expect script.exp` |

## Practice 

Try the hands-on lab for this section: [Labs/15-printing-practice.md](../Labs/15-printing-practice.md)
