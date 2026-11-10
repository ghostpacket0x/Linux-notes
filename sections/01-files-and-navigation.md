# 1. Files and navigation

Linux stores everything in folders (directories). These commands show where you are, move around, and create, copy, move, or delete files.

| Command | What it does | Example |
|---|---|---|
| `pwd` | Shows the folder you are in right now | `pwd` |
| `ls` | Lists the files and folders here | `ls` |
| `ls -l` | Long list: permissions, owner, size, and date | `ls -l` |
| `ls -a` | Includes hidden files (names that start with a dot) | `ls -a` |
| `ls -h` | With `-l`, shows sizes like 4K or 2M instead of raw bytes | `ls -lh` |
| `ls -lah` | The three above combined, a very common choice | `ls -lah` |
| `ls -F` | Adds a marker: `/` for folders, `*` for programs | `ls -F` |
| `cd <folder>` | Moves into a folder | `cd Documents` |
| `cd ..` | Goes up one folder | `cd ..` |
| `cd ~` | Goes to your home folder | `cd ~` |
| `cd /` | Goes to the very top of the system (the root folder) | `cd /` |
| `which <command>` | Shows where a command is stored | `which nmap` |
| `find . -name "<pattern>"` | Searches the current folder for names that match | `find . -name "file1*"` |
| `find / -type f` | Lists every file on the system (very long) | `find / -type f` |
| `tree` | Draws folders as a tree (you may need to install it) | `tree` |
| `touch <file>` | Creates an empty file | `touch notes.txt` |
| `mkdir <folder>` | Creates a folder | `mkdir labs` |
| `cp <from> <to>` | Copies a file | `cp notes.txt backup.txt` |
| `mv <from> <to>` | Moves a file, or renames it | `mv notes.txt labs/` |
| `rm <file>` | Deletes a file. **There is no recycle bin** | `rm backup.txt` |
| `rm -r <folder>` | Deletes a folder and everything inside it | `rm -r old-labs` |
| `rmdir <folder>` | Deletes an empty folder | `rmdir empty-folder` |
| `./script.sh` | Runs a script in the current folder. It needs permission first: `chmod +x script.sh` | `./script.sh` |

## More navigation commands

| Command | What it does | Example |
|---|---|---|
| `dir` | Lists directory contents briefly | `dir` |
| `v`, `vdir` | Lists directory contents in long format, like `ls -l -b` | `vdir` |
| `dirname <path>` | Returns the folder part of a path | `dirname /home/kali/notes.txt` |
| `whereis <command>` | Finds a command's program, source, and man page | `whereis ls` |
| `ln -s <target> <link>` | Creates a symbolic link (a shortcut) to a file | `ln -s notes.txt link.txt` |
| `locate <name>` | Finds files from a prebuilt database. Run `sudo updatedb` first if results are old | `locate notes.txt` |
| `slocate <name>` | Same as `locate` on some systems | `slocate notes.txt` |
| `mmv` | Moves or renames many files at once using patterns | `mmv "*.txt" "old_*.txt"` |
| `rename` | Renames files using a pattern | `rename 's/old/new/' *.txt` |
| `mkfifo <name>` | Creates a named pipe | `mkfifo mypipe` |
| `mknod` | Creates device or special files (needs root) | `sudo mknod mydev c 1 3` |
| `pathchk <name>` | Checks whether a file name is valid on the system | `pathchk "my file"` |
| `pushd <folder>` | Saves the current folder and changes to a new one | `pushd /etc` |
| `popd` | Returns to the folder saved by `pushd` | `popd` |
| `dirs` | Lists the folders saved by `pushd` | `dirs` |
| `dircolors` | Sets the colours that `ls` uses | `dircolors -p` |
| `open <file>` | Opens a file in its default application | `open notes.txt` |
| `man <command>` | Opens the full manual for a command | `man ls` |

Note: `symlink` appears in some reference lists, but it isn't a command. Use `ln -s` instead.
