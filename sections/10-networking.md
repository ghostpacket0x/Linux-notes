# 10. Networking

These commands help you see how a machine talks to others. They are the basics of troubleshooting and security checks.

| Command | What it does | Example |
|---|---|---|
| `ss -tulpn` | Lists listening ports. `t` TCP, `u` UDP, `l` listening, `p` which program, `n` show numbers | `sudo ss -tulpn` |
| `ss -lntp` | Listening TCP ports only | `sudo ss -lntp` |
| `netstat -a \| less` | The older tool: all connections, one page at a time | `netstat -a \| less` |
| `netstat -lt \| less` | Listening TCP ports | `netstat -lt \| less` |
| `netstat -lu` | Listening UDP ports | `netstat -lu` |
| `netstat -st` | Statistics for TCP | `netstat -st` |
| `netstat -su` | Statistics for UDP | `netstat -su` |
| `ping -c 4 <IP>` | Sends 4 test messages to check a host answers | `ping -c 4 8.8.8.8` |
| `nmap -sV <IP>` | Scans for open ports and the software behind them | `nmap -sV 127.0.0.1` |

## Interfaces and addresses with ip

Kali uses the `ip` command from the iproute2 package. It replaces the older `ifconfig`, which comes from net-tools and isn't installed by default.

| Command | What it does | Example |
|---|---|---|
| `ip addr` | Shows IP addresses for every network interface | `ip addr` |
| `ip addr show <interface>` | Shows the addresses for one interface | `ip addr show eth0` |
| `ip link` | Shows each interface and whether it is up | `ip link` |
| `sudo ip link set <interface> up` | Brings an interface up | `sudo ip link set eth0 up` |
| `sudo ip link set <interface> down` | Brings an interface down | `sudo ip link set eth0 down` |
| `ip route` | Shows the routing table, including the default gateway | `ip route` |
| `ip neigh` | Shows nearby devices the system has learned about | `ip neigh` |
| `ethtool <interface>` | Shows Ethernet card settings | `sudo ethtool eth0` |

Interface names vary between VMs, so check yours with `ip link` first. Common names are `eth0` and `enp0s3`.

> Taking an interface down can cut off your connection. Only do it on your own VM, and make sure you have a console or another way back in.

## Testing and looking up names

| Command | What it does | Example |
|---|---|---|
| `dig <name>` | DNS lookup | `dig example.com` |
| `nslookup <name>` | Queries DNS servers interactively | `nslookup example.com` |
| `traceroute <host>` | Shows the route packets take to a host | `traceroute 8.8.8.8` |
| `mtr <host>` | Network diagnostics combining traceroute and ping | `mtr 8.8.8.8` |

## Connecting and downloading

| Command | What it does | Example |
|---|---|---|
| `ssh <user>@<host>` | Logs in to another machine securely | `ssh alex@192.168.1.10` |
| `ftp <host>` | File Transfer Protocol client | `ftp 192.168.1.10` |
| `wget <url>` | Downloads a web page or file over HTTP and HTTPS | `wget https://example.com/file.txt` |

## Older tools

You'll see `ifconfig`, `ifup`, and `ifdown` in older guides. `ifconfig` comes from net-tools, and `ifup` and `ifdown` come from ifupdown. Use the `ip` commands above on Kali. Install net-tools only if you need `ifconfig` for an older guide: `sudo apt install net-tools`.

## Notes

- `netstat` is old. `ss` is the modern replacement and gives the same kind of information.
- `127.0.0.1` always means "this computer", so it is a safe address to practise `nmap` on.
- Only scan machines you own or have written permission to test.
- `rsync -e ssh` copies files to another machine over SSH. It is explained in section 3.


## Practice

Try the hands-on lab for this section: [Labs/10-networking-practice.md](../Labs/10-networking-practice.md)
