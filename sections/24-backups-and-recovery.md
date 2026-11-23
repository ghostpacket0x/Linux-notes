# 24. Backups and recovery

A backup is only useful if you can restore from it. Most people find this out at the worst possible moment, so this section covers both making copies and proving they work.

## The 3-2-1 rule

- Keep **3** copies of important data.
- Store them on **2** different types of storage, such as your laptop and an external drive.
- Keep **1** copy off-site, such as a cloud service or another location.

A copy on the same disk as the original doesn't protect you from disk failure.

## Making an archive with tar

Date-stamped names make it clear which backup is newest:

```bash
tar -czf backup-$(date +%F).tar.gz ~/notes
ls -lh backup-*.tar.gz
```

`$(date +%F)` inserts today's date, such as `2026-11-19`, into the file name.

## Copying with rsync

| Command | What it does | Example |
|---|---|---|
| `rsync -av <source>/ <destination>/` | Copies new and changed files | `rsync -av ~/notes/ /mnt/backup/notes/` |
| `rsync -av --progress <src>/ <dst>/` | Shows progress for large copies | `rsync -av --progress ~/notes/ /mnt/backup/notes/` |
| `rsync -av --delete --dry-run <src>/ <dst>/` | Shows what would be deleted, without deleting anything | `rsync -av --delete --dry-run ~/notes/ /mnt/backup/notes/` |
| `rsync -av --delete <src>/ <dst>/` | Makes the destination match the source exactly | `rsync -av --delete ~/notes/ /mnt/backup/notes/` |
| `rsync -av ~/notes/ user@host:/backups/notes/` | Copies to another machine over SSH | `rsync -av ~/notes/ alex@192.168.1.10:/backups/notes/` |

**Always run `--dry-run` first when you use `--delete`.** A wrong source path with `--delete` can remove files from your backup.

The trailing slash on the source matters. `~/notes/` copies the folder's contents. `~/notes` copies the folder itself into the destination.

## Checking the backup

A backup that you never check may be broken. Use checksums to confirm a copy matches:

| Command | What it does | Example |
|---|---|---|
| `sha256sum <file> > <file>.sha256` | Saves a checksum for a file | `sha256sum backup-2026-11-19.tar.gz > backup-2026-11-19.tar.gz.sha256` |
| `sha256sum -c <file>.sha256` | Checks the file against its saved checksum | `sha256sum -c backup-2026-11-19.tar.gz.sha256` |
| `tar -tzf <archive> \| head` | Lists the first few entries in an archive | `tar -tzf backup-2026-11-19.tar.gz \| head` |
| `diff -r <folder1> <folder2>` | Shows any differences between two folders | `diff -r ~/notes /mnt/backup/notes` |

`sha256sum -c` prints `OK` when the file matches and `FAILED` when it doesn't.

## Restoring

| Command | What it does | Example |
|---|---|---|
| `mkdir restore && tar -xzf <archive> -C restore` | Restores an archive into a separate folder | `mkdir restore && tar -xzf backup-2026-11-19.tar.gz -C restore` |
| `rsync -av /mnt/backup/notes/ ~/notes-restored/` | Restores a folder from an rsync copy | `rsync -av /mnt/backup/notes/ ~/notes-restored/` |

Restore to a new folder first, check the contents, then move them into place. Don't overwrite the only copy you have.

## Encrypting a backup

`gpg` can encrypt an archive with a passphrase:

```bash
gpg -c backup-2026-11-19.tar.gz
gpg -d backup-2026-11-19.tar.gz.gpg > restored.tar.gz
```

The first command asks you for a passphrase and creates `.gpg`. The second reverses it. Keep the passphrase somewhere safe, because without it the backup can't be opened.

## Scheduling backups

Combine this section with [section 19](19-cron-and-scheduled-tasks.md). A cron job can run the same `rsync` command every night:

```
0 2 * * * rsync -a ~/notes/ /mnt/backup/notes/ >> ~/backup.log 2>&1
```

Check `~/backup.log` regularly, because a job that fails silently gives you no backup at all.

## Notes

- Test a restore before you need it. Pick one file, restore it, and compare it with the original.
- Keep at least one backup that isn't connected to your computer, so malware or a mistake can't delete it too.
- Label backups with dates, and keep a few older versions, not just the most recent one.

## Practice

Try the hands-on lab for this section: [Labs/25-backup-practice.md](../Labs/25-backup-practice.md)
