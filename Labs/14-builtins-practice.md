# Lab 14: Shell builtins and keywords

**Goal:** try a builtin, a loop, and a variable.

**Linked section:** [14-Shell-builtins-and-keywords](../sections/14-shell-builtins-and-keywords.md)

## Steps

```bash
type ls
help cd
for i in 1 2 3; do echo "Count $i"; done
export NAME=kali
echo $NAME
```

## What to check

Each line should print what you expect. Use `help <name>` whenever you're unsure about a builtin.

## Clean up

Nothing to clean up. The variable only lasts for this terminal session.
