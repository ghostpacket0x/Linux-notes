# 3. Users and groups

Linux can have many users, and each one can belong to groups that control what they may access. Creating and removing users is a normal admin job.

## Quick reference

| Command | What it does |
|---|---|
| `whoami` | Prints the current user's name |
| `id` | Shows user and group IDs |
| `groups` | Prints the groups a user belongs to |
| `logname` | Prints the login name |
| `who` | Shows who is logged in |
| `w` | Shows who is logged in and what they are doing |
| `users` | Lists users who are logged in |
| `adduser` / `useradd` | Creates a user account |
| `usermod` | Modifies a user account |
| `deluser` / `userdel` | Deletes a user account |
| `passwd` | Changes a user's password |
| `addgroup` / `groupadd` | Creates a group |
| `groupmod` | Modifies a group |
| `delgroup` / `groupdel` | Deletes a group |
| `su` | Switches to another user |
| `sudo` | Runs a command as another user (usually root) |
| `visudo` | Edits the sudoers file safely |
| `logout` **(builtin)** | Exits a login shell |
| `write` | Sends a message to another user's terminal |

## Creating and changing users

| Command | What it does | Example |
|---|---|---|
| `sudo adduser <name>` | Creates a user with a home folder, and asks questions step by step | `sudo adduser alex` |
| `sudo useradd -m -s /bin/bash <name>` | The low-level version. `-m` makes a home folder, `-s` sets the shell | `sudo useradd -m -s /bin/bash alex` |
| `sudo passwd <name>` | Sets or changes a password | `sudo passwd alex` |
| `sudo usermod -aG <group> <name>` | Adds a user to a group. `-a` means append, so existing groups are kept | `sudo usermod -aG sudo alex` |
| `sudo usermod -L <name>` | Locks an account | `sudo usermod -L alex` |
| `sudo usermod -U <name>` | Unlocks an account | `sudo usermod -U alex` |

## Deleting users

| Command | What it does | Example |
|---|---|---|
| `sudo deluser <name>` | Deletes a user but keeps their home folder | `sudo deluser alex` |
| `sudo userdel <name>` | The low-level version of the same job | `sudo userdel alex` |

## Groups

| Command | What it does | Example |
|---|---|---|
| `sudo addgroup <group>` | Creates a group | `sudo addgroup students` |
| `sudo groupadd <group>` | The low-level way to create a group | `sudo groupadd students` |
| `sudo delgroup <group>` | Deletes a group | `sudo delgroup students` |
| `sudo groupdel <group>` | The low-level way to delete a group | `sudo groupdel students` |
| `sudo groupmod <options> <group>` | Modifies a group, for example renames it | `sudo groupmod -n staff students` |
| `groups <name>` | Prints the groups a user belongs to | `groups alex` |
| `sudo visudo` | Safely edits the file that decides who may use `sudo` | `sudo visudo` |

## Checking accounts

| Command | What it does | Example |
|---|---|---|
| `id <name>` | Shows a user's ID and groups | `id alex` |
| `getent passwd <name>` | Checks whether an account exists | `getent passwd alex` |
| `cut -d: -f1,3 /etc/passwd` | Lists every account name with its ID number | `cut -d: -f1,3 /etc/passwd` |
| `cat /etc/passwd` | Shows the list of accounts | `cat /etc/passwd` |
| `cat /etc/group` | Shows the list of groups | `cat /etc/group` |
| `sudo cat /etc/shadow` | Shows password hashes. **Never share this output** | `sudo cat /etc/shadow` |

## Logins and identity

| Command | What it does | Example |
|---|---|---|
| `whoami` | Prints the current user's name | `whoami` |
| `logname` | Prints the name you logged in with | `logname` |
| `users` | Lists the users who are logged in | `users` |
| `su <name>` | Switches to another user. Asks for that user's password | `su alex` |
| `logout` **(builtin)** | Exits a login shell | `logout` |
| `write <user>` | Sends a message to another user's terminal | `write alex` |   

## Practice 

Try the hands-on lab for this section: [Labs/03-users-practice.md](../Labs/03-users-practice.md)
