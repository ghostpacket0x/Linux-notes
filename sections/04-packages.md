# 9. Packages

A package manager is like an app store for the terminal. It downloads, installs, updates, and removes software for you. Kali uses `apt`.

## Quick reference

| Command | What it does |
|---|---|
| `apt update` | Refreshes the list of available software |
| `apt upgrade` | Installs newer versions of what you already have |
| `apt full-upgrade` | Like upgrade, but may add or remove packages when needed |
| `apt install` | Installs software |
| `apt remove` | Removes software but keeps its settings |
| `apt purge` | Removes software and its settings |
| `apt autoremove` | Removes packages only needed as dependencies |
| `apt clean` | Deletes downloaded installer files to free space |
| `apt search` | Searches for packages |
| `apt show` | Shows details about a package |
| `apt list` | Lists installed or upgradable packages |
| `dpkg -l` | Lists installed packages |
| `dpkg -s` | Shows the status of one package |
| `dpkg -L` | Lists the files a package installed |
| `dpkg -i` | Installs a downloaded `.deb` file |
| `dpkg -r` | Removes a package |
| `dpkg --configure -a` | Finishes installs that were interrupted |
| `aptitude` | Alternative upgrade tool with conflict resolution |
| `snap` | Installs apps packaged as snaps |
| `pip` | Installs Python libraries |
| `gem` | Installs Ruby libraries |
| `git` | Downloads and tracks source code |
| `make` | Compiles programs from a `Makefile` |

## The apt commands

| Command | What it does | Example |
|---|---|---|
| `sudo apt update` | Refreshes the list of available software. It does not install anything | `sudo apt update` |
| `sudo apt update --fix-missing` | Refreshes the list and retries files that failed | `sudo apt update --fix-missing` |
| `sudo apt upgrade` | Installs newer versions of what you already have | `sudo apt upgrade` |
| `sudo apt full-upgrade` | Like upgrade, but may add or remove packages when needed | `sudo apt full-upgrade` |
| `sudo apt install <pkg>` | Installs software | `sudo apt install tree` |
| `sudo apt remove <pkg>` | Removes software but keeps its settings | `sudo apt remove tree` |
| `sudo apt purge <pkg>` | Removes software and its settings | `sudo apt purge tree` |
| `-y` (added to the end) | Answers "yes" to the confirmation prompt automatically | `sudo apt full-upgrade -y` |
| `sudo apt autoremove` | Removes software that was only installed to support other software | `sudo apt autoremove` |
| `sudo apt clean` | Deletes downloaded installer files to free space | `sudo apt clean` |
| `apt search <word>` | Searches for packages | `apt search nmap` |
| `apt show <pkg>` | Shows details about a package | `apt show nmap` |
| `apt list --installed` | Lists what is installed | `apt list --installed` |
| `apt list --upgradable` | Lists what has an update waiting | `apt list --upgradable` |

## dpkg (the tool underneath apt)

| Command | What it does | Example |
|---|---|---|
| `dpkg -l` | Lists installed packages | `dpkg -l` |
| `dpkg -s <pkg>` | Shows the status of one package | `dpkg -s nmap` |
| `dpkg -L <pkg>` | Lists the files a package installed | `dpkg -L nmap` |
| `sudo dpkg -i <file>.deb` | Installs a downloaded `.deb` file | `sudo dpkg -i app.deb` |
| `sudo dpkg -r <pkg>` | Removes a package | `sudo dpkg -r app` |
| `sudo dpkg --configure -a` | Finishes installs that were interrupted | `sudo dpkg --configure -a` |

## Other tools

| Command | What it is for | Example |
|---|---|---|
| `sudo aptitude full-upgrade` | Another upgrade tool with its own way of solving conflicts | `sudo aptitude full-upgrade` |
| `snap` | Installs apps packaged as snaps | `sudo snap install code --classic` |
| `pip` | Installs Python libraries | `pip install requests` |
| `gem` | Installs Ruby libraries | `gem install bundler` |
| `git` | Downloads and tracks source code | `git clone <url>` |
| `make` | Compiles a group of programs from a `Makefile` | `make` |   
