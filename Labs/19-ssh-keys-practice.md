# Lab 19: SSH keys and configuration

**Goal:** create a key pair, check its permissions, and write a config entry.

**Linked section:** [18 SSH keys and configuration](../sections/18-ssh-keys-and-config.md)

## Steps

Use a test key name so you don't overwrite a real key:

```bash
ssh-keygen -t ed25519 -f ~/.ssh/lab_key -C "lab19"
ls -l ~/.ssh/
chmod 600 ~/.ssh/lab_key
stat -c '%a %n' ~/.ssh/lab_key
ssh -G localhost | head -5
```

Then add this to `~/.ssh/config` with `nano`, and check it with `ssh -G lab`:

```
Host lab
    HostName 127.0.0.1
    User kali
    IdentityFile ~/.ssh/lab_key
```

## What to check

- The private key should show `600` and the public key should end in `.pub`.
- `ssh -G lab` should show `hostname 127.0.0.1` and `identityfile` pointing at `lab_key`.

## Clean up

Remove the test key and the config entry:

```bash
rm ~/.ssh/lab_key ~/.ssh/lab_key.pub
```

Then delete the `Host lab` block from `~/.ssh/config`.
