# 2. Viewing and editing text

Most Linux settings and logs are plain text files. These commands let you read them, search them, and change them.

| Command | What it does | Example |
|---|---|---|
| `cat <file>` | Prints the whole file | `cat notes.txt` |
| `head <file>` | Shows the first 10 lines | `head notes.txt` |
| `tail <file>` | Shows the last 10 lines | `tail notes.txt` |
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
| `bc` | A calculator in the terminal | `echo "5*3" \| bc` |
| `whatis <command>` | Gives a one-line description of a command | `whatis ls` |
| `apropos <word>` | Finds commands related to a word | `apropos copy` |

## More text tools

| Command | What it does | Example |
|---|---|---|
| `sed 's/old/new/g' <file>` | Replaces text in a stream or file | `sed 's/bin/HTB/g' passwd.txt` |
| `gawk` | GNU version of `awk` for pattern scanning and text processing | `gawk '{print $NF}' notes.txt` |
| `egrep` | Same as `grep -E`, supports extended patterns | `egrep "error\|warn" log.txt` |
| `fgrep` | Same as `grep -F`, matches a fixed string | `fgrep "1.1.1.1" log.txt` |
| `tee <file>` | Writes output to a file and the screen | `ls \| tee list.txt` |
| `paste` | Joins lines of files side by side | `paste a.txt b.txt` |
| `join` | Joins two files on a common field | `join a.txt b.txt` |
| `nl <file>` | Numbers the lines of a file | `nl notes.txt` |
| `fold` | Wraps text to a set width | `fold -w 40 notes.txt` |
| `fmt` | Reformats paragraph text | `fmt notes.txt` |
| `rev` | Reverses each line | `echo hello \| rev` |
| `uniq` | Removes or counts repeated adjacent lines | `sort names.txt \| uniq -c` |
| `tsort` | Sorts topologically (dependency order) | `tsort deps.txt` |
| `split` | Splits a file into smaller pieces | `split -l 100 big.txt part_` |
| `seq` | Prints a sequence of numbers | `seq 1 5` |
| `expand` | Converts tabs to spaces | `expand file.txt` |
| `unexpand` | Converts spaces to tabs | `unexpand file.txt` |
| `iconv` | Converts a file's character encoding | `iconv -f latin1 -t utf8 old.txt` |
| `look <word>` | Shows lines that start with a word | `look apple words.txt` |
| `pr` | Prepares a file for printing | `pr notes.txt` |
| `more <file>` | Shows a file one screen at a time | `more notes.txt` |
| `printf` | Prints formatted text | `printf "%s\n" hello` |
| `echo` | Prints a message | `echo "hello"` |
| `diff3` | Compares three files | `diff3 a.txt b.txt c.txt` |
| `sdiff a b` | Compares two files side by side and merges them | `sdiff a.txt b.txt` |
| `xargs` | Builds a command from input lines | `find . -name "*.txt" \| xargs wc -l` |
| `yes` | Prints a string over and over until stopped | `yes \| head -3` |
| `uuencode` / `uudecode` | Encodes or decodes a binary file as text | `uuencode file.bin file.bin` |
| `vi <file>` | The original text editor (vim is its improved version) | `vi notes.txt` |
| `true` | Does nothing and succeeds (shell builtin) | `true` |
| `false` | Does nothing and fails (shell builtin) | `false` |
| `expr` | Evaluates an expression | `expr 5 + 3` |
| `read` | Reads one line of input into a variable (shell builtin) | `read name` |
| `readarray` | Reads input lines into an array (shell builtin) | `readarray -t lines < notes.txt` |


## Redirection: sending output somewhere else

Every command has three streams: input (`stdin`), normal output (`stdout`), and errors (`stderr`). Redirection changes where they go.

| Symbol | What it does | Example |
|---|---|---|
| `>` | Writes output to a file, replacing its contents | `ls > list.txt` |
| `>>` | Adds output to the end of a file | `date >> log.txt` |
| `<` | Reads input from a file | `wc -l < notes.txt` |
| `2>` | Writes errors to a file | `ls /nope 2> errors.txt` |
| `2>>` | Adds errors to the end of a file | `ls /nope 2>> errors.txt` |
| `2>&1` | Sends errors to the same place as normal output | `ls /nope > all.txt 2>&1` |
| `&>` | Sends both output and errors to one file (bash) | `ls /nope &> all.txt` |
| `2>&1 \|` | Sends errors into a pipe along with normal output | `ls /nope 2>&1 \| less` |
| `/dev/null` | A place that discards everything sent to it | `ls /nope 2>/dev/null` |
| `\|` | Sends output into another command | `ls -l \| grep txt` |
| `tee` | Shows output on screen and saves it to a file | `ls \| tee list.txt` |
| `<<<` | Gives a single string as input | `wc -w <<< "one two three"` |

### Order matters

`> file 2>&1` works, but `2>&1 > file` does not. The shell reads redirections from left to right. In `> file 2>&1`, stdout goes to the file first, then stderr follows it there. In `2>&1 > file`, stderr copies stdout's current destination (the screen) before stdout moves to the file, so errors still show on screen.

### Quick checks

- `ls > list.txt` replaces the file each time. Use `>>` if you want to keep the old lines.
- `2>/dev/null` hides error messages you don't need to read, such as "Permission denied" from a long search.
- Use `tee -a file` to append instead of replacing.

## Practice

Try the hands-on lab for this section: [Labs/02-text-practice.md](../Labs/02-text-practice.md)

Redirection practice: [Labs/23-redirection-practice.md](../Labs/23-redirection-practice.md)
