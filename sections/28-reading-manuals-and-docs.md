# 28. Reading manuals and docs

Most questions about a command can be answered on the machine itself. Knowing where the manuals are, and how to search them, is faster than searching the web and often more accurate for your version of Linux.

## Starting points

| Command | What it does | Example |
|---|---|---|
| `man <command>` | Opens the manual page for a command | `man ls` |
| `<command> --help` | Shows a short summary of options | `ls --help` |
| `whatis <command>` | Shows a one-line description | `whatis ls` |
| `apropos <word>` or `man -k <word>` | Finds manual pages that mention a word | `apropos copy` |
| `info <command>` | Opens the GNU info page, often more detailed than `man` | `info ls` |
| `help <builtin>` | Shows help for a shell builtin such as `cd` or `export` | `help cd` |

## Manual sections

Manual pages are split into numbered sections. The same name can appear in more than one section, so choose the number when you need to.

| Section | Covers | Example |
|---|---|---|
| 1 | User commands | `man 1 printf` (the shell command) |
| 2 | System calls | `man 2 printf` (the C function is in section 3) |
| 3 | Library functions | `man 3 printf` |
| 5 | File formats and configuration files | `man 5 passwd` |
| 8 | System administration commands | `man 8 useradd` |

`man 5 passwd` explains the format of `/etc/passwd` line by line, which makes the output from section 8 easier to read.

## Moving around in a man page

| Key | What it does |
|---|---|
| `Space` or `f` | Scroll forward one screen |
| `b` | Scroll back one screen |
| `/<word>` | Search forward for a word |
| `n` / `N` | Next or previous match |
| `q` | Quit |

## Reading info pages

| Key | What it does |
|---|---|
| `Enter` | Follow the link under the cursor |
| `n` / `p` | Next or previous node |
| `u` | Go up one level |
| `q` | Quit |

## Finding local documentation

Many packages install documentation in `/usr/share/doc`:

```bash
ls /usr/share/doc | head
dpkg -L <package> | grep -i doc
```

Use `dpkg -L` on an installed package to list its files, including its documentation.

## Notes

- `man` pages describe the version installed on your machine. If a web guide disagrees with `man`, trust `man` first, then check the version with `<command> --version`.
- Start with `--help` for a quick reminder, and use `man` when you need the full detail.
- Read the examples at the end of a man page. They're often the fastest way to see how options combine.

## Practice

Try the hands-on lab for this section: [Labs/29-manuals-practice.md](../Labs/29-manuals-practice.md)
