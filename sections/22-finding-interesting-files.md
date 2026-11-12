# 22. Finding interesting files

`find` searches the file system by name, type, size, age, owner, and permissions. Once you can search by permissions, you can look for things that matter on a system, such as programs that run with extra rights or folders anyone can write to.

Run broad searches with `2>/dev/null` at the end. It hides "Permission denied" messages, so the useful results are easier to see. On a system you own, or a lab you're allowed to test, these searches are standard checks.

## Basic searches

| Command | What it does | Example |
|---|---|---|
| `find <folder> -name "<pattern>"` | Finds names that match, case-sensitive | `find ~ -name "*.txt"` |
| `find <folder> -iname "<pattern>"` | Same, ignoring case | `find ~ -iname "*.TXT"` |
| `find <folder> -type f` | Regular files only | `find ~ -type f` |
| `find <folder> -type d` | Folders only | `find ~ -type d` |
| `find <folder> -type l` | Symbolic links only | `find /usr -type l` |
| `find <folder> -maxdepth 1` | Stops at one level down | `find . -maxdepth 1` |

## Searching by size and age

| Command | What it does | Example |
|---|---|---|
| `find <folder> -size +10M` | Files bigger than 10 MB | `find ~ -size +10M` |
| `find <folder> -mtime -1` | Modified in the last 24 hours | `find ~ -mtime -1` |
| `find <folder> -mmin -30` | Modified in the last 30 minutes | `find /tmp -mmin -30` |
| `find <folder> -newer <file>` | Newer than another file | `find . -newer notes.txt` |

## Searching by permissions

| Command | What it does | Example |
|---|---|---|
| `find / -perm -4000 -type f 2>/dev/null` | Files with the SUID bit set (they run with the owner's rights) | `sudo find / -perm -4000 -type f 2>/dev/null` |
| `find / -perm -2000 -type f 2>/dev/null` | Files with the SGID bit set (they run with the group's rights) | `find / -perm -2000 -type f 2>/dev/null` |
| `find / -writable -type d 2>/dev/null` | Folders the current user can write to | `find / -writable -type d 2>/dev/null` |
| `find / -perm -o+w -type f 2>/dev/null` | Files that anyone can write to | `find /tmp -perm -o+w -type f` |
| `find / -user root -perm -4000 2>/dev/null` | SUID files owned by root | `find / -user root -perm -4000 2>/dev/null` |

The `-perm -4000` form means "these bits are set". `-perm 4000` would mean "exactly this mode", which is rarely what you want.

## Acting on the results

| Command | What it does | Example |
|---|---|---|
| `find <folder> -name "*.log" -exec ls -l {} \;` | Runs a command on each match | `find /var/log -name "*.log" -exec ls -l {} \;` |
| `find <folder> -name "*.tmp" -delete` | Deletes the matches. **Check the list first without `-delete`** | `find ~/practice -name "*.tmp" -delete` |
| `find <folder> -type f \| wc -l` | Counts the files | `find ~ -type f \| wc -l` |

## Reading the output

- A SUID program owned by root is normal for tools such as `passwd` and `mount`. Look for something unusual, such as a custom program or a file in a folder you didn't expect.
- A writable folder is normal for `/tmp`. Check any other writable folder before you decide it matters.
- Use `ls -l` on each result to confirm the owner and permissions.

## Notes

- Searching `/` can take a while. Start with a smaller folder, such as `/usr/bin`, to get a feel for the output.
- Only run these searches on systems you own or have written permission to test.

## Practice

Try the hands-on lab for this section: [Labs/22-find-practice.md](../Labs/22-find-practice.md)
