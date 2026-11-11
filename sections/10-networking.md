# 10. Networking

These commands help you see how a machine talks to others. They are the basics of troubleshooting and security checks.

## Quick reference

| Command | What it does |
|---|---|
| `ss` | Shows sockets and listening ports (modern) |
| `netstat` | Shows networking information (legacy) |
| `ping` | Tests whether a host responds |
| `nmap` | Scans for open ports and services |
| `traceroute` | Shows the route packets take to a host |
| `mtr` | Network diagnostics combining traceroute and ping |
| `dig` | DNS lookup |
| `nslookup` | Queries DNS servers interactively |
| `ifconfig` | Shows or configures a network interface (legacy) |
| `ifup` | Brings a network interface up |
| `ifdown` | Brings a network interface down |
| `ethtool` | Shows and changes Ethernet card settings |
| `ssh` | Logs in to another machine securely |
| `ftp` | File Transfer Protocol client |
| `wget` | Downloads a web page or file over HTTP and HTTPS |

## Listening ports and connections

| Command | What it does | Example |
|---|---|---|
| `ss -tulpn` | Lists listening ports. `t` TCP, `u` UDP, `l` listening, `p` which program, `n` show numbers | `sudo ss -tulpn` |
| `ss -lntp` | Listening TCP ports only | `sudo ss -lntp` |
| `netstat -a \| less` | The older tool: all connections, one page at a time | `netstat -a \| less` |
| `netstat -lt \| less` | Listening TCP ports | `netstat -lt \| less` |
| `netstat -lu` | Listening UDP ports | `netstat -lu` |
| `netstat -st` | Statistics for TCP | `netstat -st` |
| `netstat -su` | Statistics for UDP | `netstat -su` |

## Connectivity and scanning

| Command | What it does | Example |
|---|---|---|
| `ping -c 4 <IP>` | Sends 4 test messages to check a host answers | `ping -c 4 8.8.8.8` |
| `nmap -sV <IP>` | Scans for open ports and the software behind them | `nmap -sV 127.0.0.1` |

## More networking commands

| Command | What it does | Example |
|---|---|---|
| `ifconfig` | Shows or configures a network interface | `ifconfig` |
| `ifup <interface>` | Brings a network interface up | `sudo ifup eth0` |
| `ifdown <interface>` | Brings a network interface down | `sudo ifdown eth0` |
| `ethtool <interface>` | Shows and changes Ethernet card settings | `sudo ethtool eth0` |
| `dig <name>` | DNS lookup | `dig example.com` |
| `nslookup <name>` | Queries DNS servers interactively | `nslookup example.com` |
| `traceroute <host>` | Shows the route packets take to a host | `traceroute 8.8.8.8` |
| `mtr <host>` | Network diagnostics combining traceroute and ping | `mtr 8.8.8.8` |
| `ssh <user>@<host>` | Logs in to another machine securely | `ssh alex@192.168.1.10` |
| `ftp <host>` | File Transfer Protocol client | `ftp 192.168.1.10` |
| `wget <url>` | Downloads a web page or file over HTTP and HTTPS | `wget https://example.com/file.txt` |

## Notes

- `netstat` is old. `ss` is the modern replacement and gives the same kind of information.
- `127.0.0.1` always means "this computer", so it is a safe address to practise `nmap` on.
- Only scan machines you own or have written permission to test.
- `rsync -e ssh` copies files to another machine over SSH. It is explained in section 3.   

## Practice 

Try the hands-on lab for this section: [Labs/10-networking-practice.md](../Labs/10-networking-practice.md)
