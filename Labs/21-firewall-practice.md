# Lab 21: Firewall basics

**Goal:** check the firewall, add and delete a rule, and read the status output. Use this only on your own VM.

**Linked section:** [20 Firewall basics](../sections/20-firewall-basics.md)

## Steps

```bash
sudo apt install ufw
sudo ufw status verbose
sudo ufw allow 8080/tcp
sudo ufw status numbered
```

Find the number of the `8080` rule, then delete it:

```bash
sudo ufw delete <number>
sudo ufw status
```

## What to check

- After `allow 8080/tcp`, the numbered list should show a rule for port 8080.
- After `delete`, the rule should be gone.

## Clean up

If you turned the firewall on, turn it off when you finish. Allow SSH first if you connect to the VM remotely:

```bash
sudo ufw disable
```

> Don't run `sudo ufw enable` on a machine you reach only over SSH unless you have allowed SSH first.
