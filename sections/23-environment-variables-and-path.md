# 23. Environment variables and PATH

An **environment variable** is a named value that programs can read, such as your home folder or the language your terminal uses. **PATH** is the most important one: it's the list of folders the shell searches when you type a command name.

## Reading variables

| Command | What it does | Example |
|---|---|---|
| `echo $HOME` | Prints the value of one variable | `echo $HOME` |
| `echo $USER` | Prints your user name | `echo $USER` |
| `echo $SHELL` | Prints the shell you're running | `echo $SHELL` |
| `printenv` | Lists all environment variables | `printenv` |
| `printenv PATH` | Prints one variable by name | `printenv PATH` |
| `env` | Lists environment variables, or runs a command with changed ones | `env \| grep HOME` |
| `set` | Lists shell variables and functions, including ones not exported | `set \| grep NAME` |

## Setting variables

| Command | What it does | Example |
|---|---|---|
| `NAME=kali` | Sets a shell variable. Only this shell can see it | `NAME=kali` |
| `export NAME=kali` | Sets a variable that child programs can also see | `export NAME=kali` |
| `unset NAME` | Removes a variable | `unset NAME` |

Test the difference:

```bash
NAME=kali
bash -c 'echo "child sees: $NAME"'      # prints nothing
export NAME=kali
bash -c 'echo "child sees: $NAME"'      # prints kali
```

## What PATH contains

```bash
echo $PATH
```

PATH is a list of folders separated by colons (`:`). When you type `ls`, the shell checks each folder from left to right and runs the first match.

| Command | What it does | Example |
|---|---|---|
| `which <command>` | Shows the file the shell will run | `which ls` |
| `type <command>` | Shows whether a name is a command, builtin, or alias | `type cd` |
| `command -v <command>` | Prints the path if the command exists, nothing if it doesn't | `command -v nmap` |

Because the first match wins, a program in an earlier folder can hide a program with the same name in a later one.

## Adding a folder to PATH

```bash
export PATH="$HOME/bin:$PATH"
```

- `$HOME/bin:$PATH` puts your folder first, so it takes priority.
- `$PATH:$HOME/bin` puts it last, so existing commands win.

This change lasts only for the current terminal. To keep it, add the line to your shell's config file.

## Making changes permanent

Kali's default shell is zsh, so the config file is `~/.zshrc`. If you use bash, the file is `~/.bashrc`.

| Command | What it does | Example |
|---|---|---|
| `echo $SHELL` | Shows which shell you use | `echo $SHELL` |
| `nano ~/.zshrc` | Opens the zsh config file | `nano ~/.zshrc` |
| `source ~/.zshrc` | Reloads the file in the current terminal | `source ~/.zshrc` |

Add lines like these to the end of the file:

```bash
export EDITOR=nano
export PATH="$HOME/bin:$PATH"
```

Then run `source ~/.zshrc` or open a new terminal.

## Notes

- **Never add `.` or an empty entry to PATH.** Either lets a program in your current folder run instead of a system command with the same name.
- **Don't leave a folder writable by others in PATH.** Anyone who can write there can add a program that runs in its place.
- `sudo` resets most variables for safety. `sudo -E` keeps yours, but avoid it unless you know why you need it.
- If a command suddenly stops working, check `echo $PATH` for a bad change.

## Practice

Try the hands-on lab for this section: [labs/23-environment-practice.md](../labs/23-environment-practice.md)
