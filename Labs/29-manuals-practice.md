# Lab 29: Reading manuals and docs

**Goal:** find the right manual page for a task, read a configuration file's format, and read an info page.

**Linked section:** [28 Reading manuals and docs](../sections/28-reading-manuals-and-docs.md)

## Steps

Find a command by a keyword, then read its manual:

```bash
apropos "copy files"
man cp
```

Inside the manual, press `/` and type `backup`, then press `n` to jump between matches. Press `q` to quit.

Read the same name from two sections:

```bash
whatis printf
man 1 printf
man 3 printf
```

Read the format of a configuration file, then look at the file itself:

```bash
man 5 passwd
head -3 /etc/passwd
```

Use the built-in help and the info page:

```bash
ls --help | head -5
info ls
```

In the info page, press `n` for the next node, `u` to go up, and `q` to quit.

## What to check

- `apropos "copy files"` should list `cp` and related commands.
- `man 1 printf` and `man 3 printf` should describe different things: the shell command and the C library function.
- `man 5 passwd` should explain the seven fields that you saw in `head -3 /etc/passwd`.
- `info ls` should open a page about the `ls` command, not an error.

## Clean up

Nothing to clean up. This lab only reads documentation.
