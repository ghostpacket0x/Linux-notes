# Lab 22: Bash scripting

**Goal:** write a script that takes an argument, checks it, and reports the result.

**Linked section:** [21 Bash scripting basics](../sections/21-bash-scripting.md)

## Steps

Create a practice folder, then the script:

```bash
mkdir -p bash-lab && cd bash-lab
echo "one" > a.txt
echo "two" > b.txt
nano check.sh
```

Paste this into `check.sh`:

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

Make it executable and run it four ways:

```bash
chmod +x check.sh
./check.sh .
./check.sh a.txt
./check.sh
echo "exit code: $?"
```

## What to check

- `./check.sh .` should count the files in the current folder.
- `./check.sh a.txt` should print the error for a file, not a folder.
- With no argument, the script should print the usage line.
- `echo "exit code: $?"` should print `1` after an error.

## Clean up

```bash
cd ~ && rm -r bash-lab
```
