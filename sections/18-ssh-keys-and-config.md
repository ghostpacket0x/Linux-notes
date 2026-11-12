# 18. SSH keys and configuration

Passwords can be guessed, but an SSH key pair is much harder to attack. You keep the **private key** on your machine, and the server keeps only the **public key**. Logging in with a key is the standard way to access servers.

## Creating a key pair

| Command | What it does | Example |
|---|---|---|
| `ssh-keygen -t ed25519 -C "<comment>"` | Creates a modern key pair in `~/.ssh/` | `ssh-keygen -t ed25519 -C "kali-lab"` |
| `ls -l ~/.ssh/` | Lists the key files | `ls -l ~/.ssh/` |
| `cat ~/.ssh/id_ed25519.pub` | Shows the public key, which is safe to share | `cat ~/.ssh/id_ed25519.pub` |

`id_ed25519` is the private key. Never share it or copy it into your notes.

## Installing the public key on a server

| Command | What it does | Example |
|---|---|---|
| `ssh-copy-id <user>@<host>` | Copies your public key to the server | `ssh-copy-id alex@192.168.1.10` |
| `ssh -i ~/.ssh/id_ed25519 <user>@<host>` | Logs in with a specific key | `ssh -i ~/.ssh/id_ed25519 alex@192.168.1.10` |

## Permissions on the SSH folder

SSH refuses to use keys that other users can read, so the permissions matter.

| Path | Permission | Command |
|---|---|---|
| `~/.ssh` | Folder, only you | `chmod 700 ~/.ssh` |
| Private key | Only you can read it | `chmod 600 ~/.ssh/id_ed25519` |
| Public key and config | Readable by you | `chmod 644 ~/.ssh/id_ed25519.pub` |

## Client configuration

The file `~/.ssh/config` saves connection details, so you don't type them each time.

```
Host lab
    HostName 192.168.1.10
    User alex
    IdentityFile ~/.ssh/id_ed25519
```

After that, `ssh lab` connects with the right user and key.

## Notes

- Use a passphrase on your private key, so a stolen file isn't enough on its own.
- Only connect to machines you own or have permission to access.
- To check the connection details SSH will use, run `ssh -G lab`.

## Practice 

Try the hands-on lab for this section: [Labs/18-ssh-keys-practice.md](../Labs/18-ssh-keys-practice.md)
