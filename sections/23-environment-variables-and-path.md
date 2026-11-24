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

## Shell customisation

Small changes to your shell make everyday work faster. Keep all of them in `~/.zshrc` so they survive a restart.

### Aliases

An alias is a short name for a longer command.

```bash
alias ll='ls -lah'
alias up='cd ..'
alias ports='sudo ss -tulpn'
```

| Command | What it does | Example |
|---|---|---|
| `alias <name>='<command>'` | Creates an alias for this session | `alias ll='ls -lah'` |
| `alias` | Lists all aliases | `alias` |
| `type <name>` | Shows whether a name is an alias | `type ll` |
| `unalias <name>` | Removes an alias | `unalias ll` |

Notes on aliases:

- Aliases work only in your interactive shell. Scripts don't read them, so use functions or full commands in scripts.
- `alias rm='rm -i'` asks before each deletion. It's a useful habit, but people who rely on it may be caught out on a machine without it.

### Prompts

The prompt is set by the `PROMPT` variable in zsh (or `PS1` in bash). Zsh uses `%` codes:

| Code | Shows |
|---|---|
| `%n` | Your user name |
| `%m` | The host name |
| `%~` | The current folder, shortened with `~` for home |
| `%#` | `#` for root, `%` for a normal user |

```bash
PROMPT='%n@%m %~ %# '
```

Bash uses `\u`, `\h`, `\w`, and `\$` for the same things, for example `PS1='\u@\h \w \$ '`.

### Organising ~/.zshrc

- Group related lines under a comment heading, such as `# aliases` or `# PATH`.
- Put `export` lines for PATH and variables before the aliases that use them.
- Reload after each change with `source ~/.zshrc`, or open a new terminal.

### Safe changes

```bash
cp ~/.zshrc ~/.zshrc.bak
nano ~/.zshrc
```

If the terminal breaks after an edit, start a shell without loading your config, restore the backup, and reload:

```bash
zsh -f
cp ~/.zshrc.bak ~/.zshrc
```

### History settings

| Variable | What it does | Example |
|---|---|---|
| `HISTSIZE` | Commands kept in memory for this session | `HISTSIZE=5000` |
| `SAVEHIST` | Commands saved to the history file | `SAVEHIST=5000` |
| `HISTFILE` | Where the history is saved | `HISTFILE=~/.zsh_history` |

## Practice

Try the hands-on lab for this section: [Labs/24-environment-practice.md](../Labs/24-environment-practice.md)
