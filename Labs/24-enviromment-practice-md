# Lab 24: Environment variables and PATH

**Goal:** make a small command, see it fail when its folder isn't in PATH, then add the folder and run it.

**Linked section:** [23 Environment variables and PATH](../sections/23-environment-variables-and-path.md)

## Steps

Create a tiny program in a folder called `~/bin`:

```bash
mkdir -p ~/bin
printf '#!/bin/bash\necho "hello from my tool"\n' > ~/bin/hello-lab
chmod +x ~/bin/hello-lab
```

Check whether the shell can find it:

```bash
echo $PATH
hello-lab
```

Some systems add `~/bin` to PATH automatically when the folder exists, so `hello-lab` may already work. If that happens, the lab still works. Skip the export step, and check that `echo $PATH` lists `/home/<you>/bin`.

If `hello-lab` says "command not found", add the folder to PATH for this terminal and try again:

```bash
export PATH="$HOME/bin:$PATH"
hello-lab
which hello-lab
```

## What to check

- Before the export, `which hello-lab` should print nothing, unless `~/bin` was already in PATH.
- After the export, `hello-lab` should print `hello from my tool`, and `which` should show `/home/<you>/bin/hello-lab`.
- Open a new terminal and run `echo $PATH`. If `~/bin` is missing from it, the export lasted only for the earlier terminal, which is what this lab is meant to show. If it's still there, your system adds `~/bin` automatically, and that's fine.

## Clean up

```bash
rm ~/bin/hello-lab
rmdir ~/bin 2>/dev/null
```

`rmdir` only removes `~/bin` if it's empty. If you added the PATH line to `~/.zshrc`, remove it from that file as well.
