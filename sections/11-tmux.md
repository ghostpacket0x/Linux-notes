
# 11. Terminal multiplexing with tmux

`tmux` lets you split one terminal window into several panes and keep sessions running even if you close the window. This is useful for long jobs such as system upgrades.

Start it with `tmux`. After that, every shortcut begins with `Ctrl+b`: press `Ctrl+b`, let go, then press the next key.

## Quick reference

| Command | What it does |
|---|---|
| `tmux` | Starts a session |
| `tmux ls` | Lists open sessions |
| `tmux attach -t <name>` | Reconnects to a session |
| `Ctrl+b` then `%` | Splits the window left/right |
| `Ctrl+b` then `"` | Splits the window top/bottom |
| `Ctrl+b` then arrows / `o` | Moves between panes |
| `Ctrl+b` then `x` | Closes the current pane |
| `Ctrl+b` then `d` | Detaches (session keeps running) |
| `Ctrl+b` then `:` | Enters command mode |

## Key bindings and commands

| Keys or command | What it does |
|---|---|
| `tmux` | Starts a session |
| `Ctrl+b` then `%` | Splits the window into left and right panes |
| `Ctrl+b` then `"` | Splits the window into top and bottom panes |
| `Ctrl+b` then arrow keys, or `o` | Moves between panes |
| `Ctrl+b` then `x` | Closes the current pane |
| `Ctrl+b` then `d` | Detaches: leaves the session running in the background |
| `tmux attach -t <name>` | Reconnects to a session. Use `tmux ls` to see session names |
| `Ctrl+b` then `:` and `set -g status off` | Hides the status bar at the bottom |

To hide the status bar every time, add `set -g status off` to `~/.tmux.conf`.   

## Practice 

Try the hands-on lab for this section: [Labs/11-tmux-practice.md](../Labs/11-tmux-practice.md)
