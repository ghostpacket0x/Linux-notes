# 20. Firewall basics

A firewall decides which network connections a machine accepts. `ufw` (Uncomplicated Firewall) is a simple front end for the firewall rules on Debian-based systems such as Kali.

> Changing firewall rules can lock you out of a remote machine. Only change rules on your own VM, and allow SSH before you enable the firewall if you use SSH.

## Checking and installing

| Command | What it does | Example |
|---|---|---|
| `sudo apt install ufw` | Installs ufw | `sudo apt install ufw` |
| `sudo ufw status` | Shows whether the firewall is on and its rules | `sudo ufw status` |
| `sudo ufw status verbose` | Adds the default policies | `sudo ufw status verbose` |
| `sudo ufw status numbered` | Lists rules with numbers, so you can delete one | `sudo ufw status numbered` |

## Allowing and denying traffic

| Command | What it does | Example |
|---|---|---|
| `sudo ufw default deny incoming` | Blocks incoming traffic unless a rule allows it | `sudo ufw default deny incoming` |
| `sudo ufw default allow outgoing` | Allows outgoing traffic | `sudo ufw default allow outgoing` |
| `sudo ufw allow OpenSSH` | Allows SSH connections | `sudo ufw allow OpenSSH` |
| `sudo ufw allow 80/tcp` | Allows web traffic on port 80 | `sudo ufw allow 80/tcp` |
| `sudo ufw deny 23/tcp` | Blocks Telnet | `sudo ufw deny 23/tcp` |
| `sudo ufw delete <number>` | Deletes a rule by its number | `sudo ufw delete 2` |

## Turning it on and off

| Command | What it does |
|---|---|
| `sudo ufw enable` | Turns the firewall on |
| `sudo ufw disable` | Turns the firewall off |
| `sudo ufw reset` | Removes all rules. Use with care |

## Notes

- Check the rules with `sudo ufw status` after each change.
- `ss -tulpn` shows which ports are listening, so you can compare them with your firewall rules (section 7).

## Practice

