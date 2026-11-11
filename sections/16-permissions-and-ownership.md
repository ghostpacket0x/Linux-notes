# 16. Permissions and ownership

Every file and folder has an owner, a group, and a set of permissions. Permissions decide who can read, change, or run a file. Most security and admin problems come down to permissions, so it's worth learning them early.

## Reading the permission string

```bash
ls -l notes.txt
# -rw-r--r-- 1 kali kali 120 Nov 10 13:00 notes.txt
```

| Part | Meaning |
|---|---|
| First character | The type: `-` file, `d` folder, `l` link |
| Next three | Permissions for the **owner** |
| Next three | Permissions for the **group** |
| Last three | Permissions for **everyone else** |

Each permission is a letter, or a dash when it's missing:

| Letter | Number | On a file | On a folder |
|---|---|---|---|
| `r` | 4 | Read the contents | List the names inside |
| `w` | 2 | Change the contents | Add, rename, or delete items |
| `x` | 1 | Run it as a program | Enter the folder (`cd` into it) |

Add the numbers in each group to get the octal value. For example, `rw-r--r--` is `6 4 4`.

## Changing permissions with chmod

| Command | What it does | Example |
|---|---|---|
| `chmod 644 <file>` | Owner can read and write, everyone else can read | `chmod 644 notes.txt` |
| `chmod 755 <file>` | Owner can read, write, and run, everyone else can read and run | `chmod 755 script.sh` |
| `chmod u+x <file>` | Adds execute for the owner | `chmod u+x script.sh` |
| `chmod g-w <file>` | Removes write for the group | `chmod g-w notes.txt` |
| `chmod o-rwx <file>` | Removes all access for everyone else | `chmod o-rwx secret.txt` |
| `chmod -R 755 <folder>` | Applies the change to a folder and everything inside it | `chmod -R 755 site/` |

`u` is the owner, `g` is the group, `o` is others, and `a` is all three.

## Changing owner and group

| Command | What it does | Example |
|---|---|---|
| `sudo chown <user> <file>` | Changes the owner | `sudo chown alex notes.txt` |
| `sudo chown <user>:<group> <file>` | Changes the owner and group together | `sudo chown alex:students notes.txt` |
| `sudo chgrp <group> <file>` | Changes only the group | `sudo chgrp students notes.txt` |
| `sudo chown -R <user> <folder>` | Changes the owner of a folder and everything inside | `sudo chown -R alex site/` |

## Checking permissions in detail

| Command | What it does | Example |
|---|---|---|
| `stat -c '%a %U %G %n' <file>` | Shows the octal mode, owner, group, and name | `stat -c '%a %U %G %n' notes.txt` |
| `umask` | Shows the default permissions for new files (shell builtin) | `umask` |
| `ls -ld <folder>` | Shows a folder's own permissions, not its contents | `ls -ld /tmp` |

`/tmp` shows a `t` at the end of its permission string, which is the sticky bit. It lets anyone create files there but stops users from deleting each other's files.

## Special permissions

- **SUID** (`s` in the owner's execute slot) makes a program run with its owner's rights, not the user's. `passwd` uses this so you can change your own password.
- You can find SUID files with `find / -perm -4000 -type f 2>/dev/null`. Learn to read the output, and only search systems you own or are allowed to test.

## Notes

- Permissions on a folder control access to its contents. A folder with no `x` can't be entered, even if its files are readable.
- Avoid `chmod 777`. It gives everyone full access and usually hides a real problem.

## Practice

Try the hands-on lab for this section: [labs/17-permissions-practice.md](../labs/17-permissions-practice.md)
