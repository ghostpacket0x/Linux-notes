# 3. Archives and rsync

## Quick reference

| Command | What it does |
|---|---|
| `tar` | Creates, lists, and extracts archives |
| `zip` / `unzip` | Creates and extracts zip archives |
| `rsync` | Copies files and keeps them in sync, locally or over SSH |
| `scp` | Copies files securely to or from another machine over SSH |
| `sftp` | Interactive secure file transfer over SSH |
| `rcp` | Copies files between machines (older, unencrypted) |
| `install` | Copies files and sets permissions in one step |
| `sum` | Prints a checksum for a file |
| `unshar` | Unpacks shell archive scripts |

## Archives (bundling files together)

An archive packs many files into one file, which is useful for backups.

| Command | What it does | Example |
|---|---|---|
| `tar -czf <name>.tar.gz <folder>` | Creates a compressed archive. `c` = create, `z` = compress, `f` = file name | `tar -czf backup.tar.gz labs/` |
| `tar -tf <archive>` | Lists what is inside without extracting | `tar -tf backup.tar.gz` |
| `tar -xzf <archive>` | Extracts an archive. `x` = extract | `tar -xzf backup.tar.gz` |
| `zip -r <name>.zip <folder>` | Creates a zip file. `-r` includes subfolders | `zip -r backup.zip labs/` |
| `unzip <file>.zip` | Extracts a zip file | `unzip backup.zip` |
| `unzip -l <file>.zip` | Lists the contents of a zip without extracting | `unzip -l backup.zip` |

## Copying and syncing with rsync

`rsync` copies files like `cp`, but it only transfers what has changed, so repeat backups are fast. It can also copy to another computer over SSH.

| Command | What it does | Example |
|---|---|---|
| `rsync -a <from>/ <to>/` | Archive mode: copies folders and keeps permissions, dates, and links | `rsync -a labs/ backup/` |
| `rsync -v` | Verbose: shows each file as it is copied | `rsync -av labs/ backup/` |
| `rsync -z` | Compresses data while it travels, which helps on slow connections | `rsync -avz labs/ backup/` |
| `rsync -P` | Shows a progress bar and allows resuming interrupted transfers | `rsync -avzP labs/ backup/` |
| `rsync -e ssh` | Sends the files through SSH to another machine | `rsync -a -e ssh labs/ user@192.168.1.10:/home/user/labs/` |
| `rsync --delete` | Makes the destination an exact mirror by deleting files that are no longer in the source | `rsync -a --delete labs/ backup/` |

Notes:

- A slash at the end of the source (`labs/`) means "copy what is inside the folder". Without it, rsync copies the folder itself.
- `--delete` removes files, so test first with `--dry-run`, which shows what would happen without doing it: `rsync -a --delete --dry-run labs/ backup/`.
- Only copy to machines you own or have permission to use.

## Other copy tools

| Command | What it does | Example |
|---|---|---|
| `scp` | Copies files securely to or from another machine over SSH | `scp notes.txt user@host:/home/user/` |
| `scp -r` | Recursively copies a directory | `scp -r labs/ user@host:/home/user/` |
| `sftp` | Interactive secure file transfer over SSH | `sftp user@host` |
| `rcp` | Copies files between machines. Older and unencrypted, so avoid it | `rcp a.txt host:/tmp/` |
| `install` | Copies files and sets their permissions in one step | `sudo install -m 755 script.sh /usr/local/bin/` |
| `sum <file>` | Prints a checksum for a file, useful for checking a copy | `sum notes.txt` |
| `unshar` | Unpacks shell archive scripts | `unshar archive.shar` |   
