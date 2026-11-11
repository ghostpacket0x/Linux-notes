# 14. Shell builtins and keywords

Builtins are part of the shell itself, so use `help <name>` for them instead of `man`. Keywords are part of shell scripting syntax and are used inside scripts or loops.

## Builtins

| Builtin | What it does | Example |
|---|---|---|
| `enable` | Turns builtin commands on or off | `enable -n echo` |
| `eval` | Runs its arguments as a shell command | `eval "echo hi"` |
| `exec` | Replaces the shell with another command | `exec ls` |
| `exit` | Closes the shell | `exit` |
| `export` | Makes a variable available to child processes | `export NAME=kali` |
| `hash` | Remembers the full path of commands you've run | `hash` |
| `help` | Shows help for a builtin | `help cd` |
| `history` | Lists previous commands | `history` |
| `let` | Does arithmetic on shell variables | `let x=5+2` |
| `local` | Creates a variable that exists only inside a function | `local count=0` |
| `return` | Leaves a shell function with a status | `return 0` |
| `select` | Builds a numbered menu from a list of options | `select f in a b c; do echo $f; break; done` |
| `set` | Shows or changes shell options and positional parameters | `set -- one two` |
| `shift` | Moves positional parameters one place to the left | `shift` |
| `shopt` | Turns shell options on or off | `shopt -s nullglob` |
| `source` | Runs commands from a file in the current shell (same as `.`) | `source ~/.bashrc` |
| `test` | Checks a condition (same as `[ ]`) | `test -f notes.txt && echo yes` |
| `type` | Shows whether a name is a command, builtin, or alias | `type ls` |
| `ulimit` | Shows or sets resource limits for the shell | `ulimit -a` |
| `umask` | Shows or sets the default permissions for new files | `umask` |
| `unalias` | Removes an alias | `unalias ll` |
| `unset` | Removes a variable or function | `unset NAME` |
| `getopts` | Parses options for a shell script | `getopts "ab:" opt` |
| `function` | Defines a shell function | `function greet { echo hi; }` |

## Keywords

| Keyword | What it does |
|---|---|
| `if` | Runs commands only when a condition is true |
| `for` | Repeats commands for each item in a list |
| `while` | Repeats commands as long as a condition is true |
| `until` | Repeats commands until a condition becomes true |

Example:

```bash
for user in alice bob; do
    echo "Hello $user"
done
```

## Practice 

Try the hands-on lab for this section: [Labs/14-builtins-practice.md](../Labs/14-builtins-practice.md)
