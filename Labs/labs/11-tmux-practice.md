# Lab 11: Terminal multiplexing with tmux

**Goal:** start a session, split it, detach, and come back.

**Linked section:** [11 Terminal multiplexing with tmux](../sections/11-tmux.md)

## Steps

```bash
tmux
```

Then:

1. Press `Ctrl+b`, let go, then `%` to split the window.
2. Press `Ctrl+b`, let go, then `d` to detach.
3. Run `tmux ls` to see the session.
4. Run `tmux attach` to return to it.

## What to check

`tmux ls` should show one session, and the split should still be there after you reattach.

## Clean up

Type `exit` in each pane to close the session.
