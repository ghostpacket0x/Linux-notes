# 21. Bash scripting basics

A shell script is a text file of commands that the shell runs in order. Scripts let you repeat a task, pass in values, and make decisions. You've already used a loop and `./script.sh`, so this section fills in the rest.

## Writing and running a script

```bash
nano hello.sh
```

```bash
#!/bin/bash
# The first line tells Linux which shell runs this file
echo "Hello from a script"
```

| Command | What it does | Example |
|---|---|---|
| `chmod +x hello.sh` | Makes the file executable | `chmod +x hello.sh` |
| `./hello.sh` | Runs the script from the current folder | `./hello.sh` |
| `bash hello.sh` | Runs it without making it executable | `bash hello.sh` |

Lines that start with `#` are comments. The `#!/bin/bash` line is not a comment; it's the shebang.

## Variables

```bash
name="kali"
echo "Hello, $name"
echo "Your home is $HOME"
```

- No spaces around the `=` sign.
- Use `$name` to read a variable.
- Quote your variables (`"$name"`) so values with spaces still work.

## Arguments

When you run `./script.sh one two`, the script can read the values it was given.

| Variable | Meaning |
|---|---|
| `$0` | The script's own name |
| `$1`, `$2` | The first and second arguments |
| `$#` | How many arguments were given |
| `$@` | All the arguments |
| `$?` | The exit code of the last command (`0` means success) |

## Making decisions with if

```bash
if [ -f "$1" ]; then
    echo "$1 is a file"
elif [ -d "$1" ]; then
    echo "$1 is a folder"
else
    echo "$1 does not exist"
fi
```

| Test | True when |
|---|---|
| `-f file` | The file exists and is a regular file |
| `-d folder` | The folder exists |
| `-e path` | Anything exists at that path |
| `-eq`, `-lt`, `-gt` | Numbers are equal, less than, or greater than |
| `=`, `!=` | Strings are equal, or not equal |

## Loops

```bash
for file in *.txt; do
    echo "Found $file"
done

count=1
while [ "$count" -le 3 ]; do
    echo "Pass $count"
    count=$((count + 1))
done
```

## Command substitution

`$(...)` runs a command and uses its output:

```bash
today=$(date +%F)
echo "Backup for $today"
```

## Exit codes and safe settings

- `exit 0` ends the script with success. `exit 1` signals an error.
- `set -euo pipefail` near the top stops the script on errors, undefined variables, and failed pipes. It's a good habit for scripts that change files.

## Example: check a folder

```bash
#!/bin/bash
set -euo pipefail

if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <folder>"
    exit 1
fi

if [ ! -d "$1" ]; then
    echo "Error: $1 is not a folder"
    exit 1
fi

echo "$1 contains $(ls -1 "$1" | wc -l) items"
```

## Notes

- Test scripts in a practice folder first. A script that deletes files can't be undone.
- Use `shellcheck` to find common mistakes: `sudo apt install shellcheck`, then `shellcheck script.sh`.

## Practice

Try the hands-on lab for this section: [labs/22-bash-practice.md](../labs/22-bash-practice.md)
