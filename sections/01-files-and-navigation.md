# 1. Files and navigation

Linux stores everything in folders (directories). These commands show where you are, move around, and create, copy, move, or delete files.

Tip: check any command with `whatis <cmd>` or `man <cmd>`. Commands marked **(builtin)** are part of the shell, so use `help <cmd>` instead of `man`.

## Basics

| Command | What it does | Example |
|---|---|---|
| `pwd` | Shows the folder you are in right now | `pwd` |
| `ls` | Lists the files and folders here | `ls` |
| `ls -l` | Long list: permissions, owner, size, and date | `ls -l` |
| `ls -a` | Includes hidden files (names that start with a dot) | `ls -a` |
| `ls -h` | With `-l`, shows sizes like 4K or 2M instead of raw bytes | `ls -lh` |
| `ls -lah` | Long list, hidden files, and readable sizes combined | `ls -lah` |
| `ls -F` | Adds a marker: `/` folder, `*` executable, `@` symbolic link, `\|` named pipe | `ls -F` |
| `cd <folder>` | Moves into a folder | `cd Documents` |
| `cd ..` | Goes up one folder | `cd ..` |
| `cd ~` | Goes to your home folder | `cd ~` |
| `cd /` | Goes to the top of the system (the root folder) | `cd /` |
| `which <command>` | Shows where a command is stored | `which ls` |
| `find . -name "<pattern>"` | Searches the current folder for matching names | `find . -name "file1*"` |
| `find / -type f` | Lists every file on the system (very long, so page it) | `find / -type f \| less` |
| `tree` | Draws folders as a tree (you may need to install it) | `tree` |
| `touch <file>` | Creates an empty file or updates its timestamp | `touch notes.txt` |
| `mkdir <folder>` | Creates a folder | `mkdir labs` |
| `cp <from> <to>` | Copies a file | `cp notes.txt backup.txt` |
| `cp -r <folder> <to>` | Copies a folder and everything inside it | `cp -r labs labs-backup` |
| `mv <from> <to>` | Moves a file, or renames it | `mv notes.txt labs/` |
| `rm <file>` | Deletes a file. **There is no recycle bin** | `rm backup.txt` |
| `rm -r <folder>` | Deletes a folder and everything inside it | `rm -r old-labs` |
| `rmdir <folder>` | Deletes an empty folder | `rmdir empty-folder` |
| `./script.sh` | Runs a script in the current folder. It needs permission first: `chmod +x script.sh` | `./script.sh` |

## More navigation commands

| Command | What it does | Example |
|---|---|---|
| `dir` | Lists directory contents in columns (like `ls -C -b`) | `dir` |
| `vdir` | Lists directory contents in long format (like `ls -l -b`) | `vdir` |
| `file <name>` | Tells you what type of file something is | `file notes.txt` |
| `dirname <path>` | Returns the folder part of a path | `dirname /home/kali/notes.txt` |
| `whereis <command>` | Finds a command's program, source, and man page | `whereis ls` |
| `ln -s <target> <link>` | Creates a symbolic link (a shortcut) to a file | `ln -s notes.txt link.txt` |
| `locate <name>` | Finds files from a prebuilt database. Run `sudo updatedb` first if results are old | `locate notes.txt` |
| `plocate` / `mlocate` | Modern versions of `locate`. They replaced the obsolete `slocate` | `plocate notes.txt` |
| `mmv` | Moves or renames many files using patterns. Install it first; `#1` means what the first `*` matched | `mmv "*.txt" "old_#1.txt"` |
| `rename` | Renames files using a pattern. Syntax differs by distro (Perl version on Kali/Debian/Ubuntu, util-linux version on Fedora/RHEL) | `rename 's/old/new/' *.txt` |
| `pathchk <name>` | Checks whether a file name is valid on the system (prints nothing if it is) | `pathchk "my file"` |
| `pushd <folder>` **(builtin)** | Saves the current folder and changes to a new one | `pushd /etc` |
| `popd` **(builtin)** | Returns to the folder saved by `pushd` | `popd` |
| `dirs` **(builtin)** | Lists the folders saved by `pushd` | `dirs` |
| `dircolors` | Shows or sets the colours `ls` uses (`-p` prints the defaults) | `dircolors -p` |
| `xdg-open <file>` | Opens a file in its default application (Linux; `open` is macOS only) | `xdg-open notes.txt` |
| `man <command>` | Opens the full manual for a command | `man ls` |

## Advanced (rarely needed)

| Command | What it does | Example |
|---|---|---|
| `mkfifo <name>` | Creates a named pipe | `mkfifo mypipe` |
| `mknod` | Creates device or special files. Needs root and is easy to get wrong | `sudo mknod mydev c 1 3` |

Notes:
- `symlink` is not a command. Use `ln -s`.
- `v` is not a standard command. It only exists as an alias on some systems, so use `vdir`.
