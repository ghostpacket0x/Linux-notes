# 2. Viewing and editing text

Most Linux settings and logs are plain text files. These commands let you read them, search them, and change them.

Tip: check any command with `whatis <cmd>` or `man <cmd>`. Commands marked **(builtin)** are part of the shell, so use `help <cmd>` instead of `man`. The examples assume the files (`notes.txt`, `log.txt`, ...) exist, so create some test files first.

## Basics

| Command | What it does | Example |
|---|---|---|
| `cat <file>` | Prints the whole file | `cat notes.txt` |
| `head <file>` | Shows the first 10 lines | `head notes.txt` |
| `tail <file>` | Shows the last 10 lines (`tail -f` keeps following new lines) | `tail notes.txt` |
| `less <file>` | Lets you scroll through a long file. Press `q` to quit | `less notes.txt` |
| `nano <file>` | A beginner-friendly editor. `Ctrl+O` then Enter saves, `Ctrl+X` exits | `nano notes.txt` |
| `vim <file>` | A powerful editor. Press `i` to type, then `Esc` and `:wq` to save and quit, or `:q!` to quit without saving | `vim notes.txt` |
| `grep "<word>" <file>` | Shows the lines that contain a word | `grep "error" log.txt` |
| `grep -A3 "<word>" <file>` | Also shows 3 lines after each match | `grep -A3 "error" log.txt` |
| `sort <file>` | Sorts the lines alphabetically | `sort names.txt` |
| `tr 'a-z' 'A-Z'` | Swaps characters. This example makes text uppercase | `echo hello \| tr 'a-z' 'A-Z'` |
| `strings <file>` | Pulls readable text out of a program or binary file | `strings /bin/ls` |
| `file "<name>"` | Tells you what type of file something is | `file notes.txt` |
| `wc <file>` | Counts lines, words, and bytes | `wc notes.txt` |
| `wc -c <file>` | Counts bytes only | `wc -c notes.txt` |
| `wc -L <file>` | Shows the length of the longest line | `wc -L notes.txt` |
| `awk '{print $1}' <file>` | Prints the first word (column) of every line | `awk '{print $1}' notes.txt` |
| `cut -d: -f1 <file>` | Splits each line at `:` and prints field 1 | `cut -d: -f1 /etc/passwd` |
| `bc` | A calculator in the terminal (install it if missing) | `echo "5*3" \| bc` |
| `whatis <command>` | Gives a one-line description of a command (needs the man page database) | `whatis ls` |
| `apropos <word>` | Finds commands related to a word (needs the man page database; run `sudo mandb` if empty) | `apropos copy` |

## More text tools

| Command | What it does | Example |
|---|---|---|
| `sed 's/old/new/g' <file>` | Replaces text in a stream or file | `sed 's/bin/HTB/g' passwd.txt` |
| `gawk` | GNU version of `awk` for pattern scanning and text processing (install it if missing) | `gawk '{print $NF}' notes.txt` |
| `grep -E` / `egrep` | Extended patterns. `egrep` is deprecated, prefer `grep -E` | `grep -E "error\|warn" log.txt` |
| `grep -F` / `fgrep` | Fixed string, no pattern characters. `fgrep` is deprecated, prefer `grep -F` | `grep -F "1.1.1.1" log.txt` |
| `more <file>` | Shows a file one screen at a time (simpler than `less`) | `more notes.txt` |
| `vi <file>` | The original text editor (vim is its improved version) | `vi notes.txt` |
| `look <word> <file>` | Shows lines that start with a word (the file must be sorted; may need installing) | `look apple words.txt` |
| `nl <file>` | Numbers the lines of a file | `nl notes.txt` |
| `rev` | Reverses each line | `echo hello \| rev` |
| `uniq` | Removes or counts repeated **adjacent** lines, so sort first | `sort names.txt \| uniq -c` |
| `tee <file>` | Writes output to a file and the screen | `ls \| tee list.txt` |
| `xargs` | Builds a command from input lines | `find . -name "*.txt" -print0 \| xargs -0 wc -l` |
| `fold` | Wraps text to a set width | `fold -w 40 notes.txt` |
| `fmt` | Reformats paragraph text | `fmt notes.txt` |
| `expand` | Converts tabs to spaces | `expand file.txt` |
| `unexpand` | Converts spaces to tabs (only leading spaces unless you add `-a`) | `unexpand -a file.txt` |
| `paste` | Joins lines of files side by side | `paste a.txt b.txt` |
| `join` | Joins two files on a common field (both must be sorted on it) | `join a.txt b.txt` |
| `split` | Splits a file into smaller pieces | `split -l 100 big.txt part_` |
| `diff3` | Compares three files | `diff3 a.txt b.txt c.txt` |
| `sdiff a b` | Compares two files side by side (`-o <file>` merges them interactively) | `sdiff a.txt b.txt` |
| `echo` | Prints a message | `echo "hello"` |
| `printf` | Prints formatted text | `printf "%s\n" hello` |
| `seq` | Prints a sequence of numbers | `seq 1 5` |
| `yes` | Prints a string over and over until stopped (`Ctrl+C`) | `yes \| head -3` |

## Shell scripting helpers

| Command | What it does | Example |
|---|---|---|
| `expr` | Evaluates an expression | `expr 5 + 3` |
| `export` **(builtin)** | Sets an environment variable for child programs | `export EDITOR=vim` |
| `read` **(builtin)** | Reads one line of input into a variable | `read name` |
| `readarray` **(builtin)** | Reads input lines into an array | `readarray -t lines < notes.txt` |
| `readonly` **(builtin)** | Marks a variable as unchangeable | `readonly PI=3.14` |
| `getopts` **(builtin)** | Parses options inside a shell script | `while getopts "ab:" opt; do echo "$opt"; done` |
| `true` | Does nothing and succeeds (exit status 0) | `true; echo $?` |
| `false` | Does nothing and fails (exit status 1) | `false; echo $?` |

## Advanced (rarely needed)

| Command | What it does | Example |
|---|---|---|
| `iconv` | Converts a file's character encoding | `iconv -f latin1 -t utf8 old.txt > new.txt` |
| `pr` | Prepares a file for printing | `pr notes.txt` |
| `tsort` | Sorts topologically (dependency order) | `tsort deps.txt` |
| `uuencode` / `uudecode` | Encodes or decodes a binary file as text (needs the `sharutils` package) | `uuencode file.bin file.bin > file.uu` |

Notes:
- `egrep` and `fgrep` still work, but newer GNU grep prints a warning, so prefer `grep -E` and `grep -F`.
- `true` and `false` exist both as shell builtins and as separate programs, so `man` has a page for them.
- On Debian-based systems such as Kali, plain `awk` is often `mawk`. Install `gawk` if you need the GNU features.
- `file` also appears in section 01. It is repeated here so each section reads on its own.
- `fdformat` (a floppy disk formatter) is obsolete and left out.

## Practice

Try the hands-on lab for this section: [Labs/02-text-practice.md](../Labs/02-text-practice.md)
