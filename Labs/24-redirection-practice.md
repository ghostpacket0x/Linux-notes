# Lab 24: Redirection and pipes

**Goal:** send output and errors to files, read input from a file, and combine commands with pipes.

**Linked section:** [02 Viewing and editing text](../sections/02-text-and-viewing.md)

## Steps

```bash
mkdir -p redirect-lab && cd redirect-lab
ls > list.txt
ls /nope 2> errors.txt
ls /nope > all.txt 2>&1
ls /nope 2>/dev/null; echo "exit code: $?"
wc -l < list.txt
echo "one two three" >> words.txt
echo "four five" >> words.txt
wc -w words.txt
ls -l | grep txt | tee txt-files.txt
```

## What to check

- `errors.txt` should contain the "No such file or directory" message.
- `all.txt` should also contain that message, because `2>&1` sent errors there too.
- The `2>/dev/null` line should print nothing for the error, then `exit code: 2`.
- `wc -w words.txt` should report 5 words.
- `txt-files.txt` should match what appears on screen.

## Clean up

```bash
cd ~ && rm -r redirect-lab
```
