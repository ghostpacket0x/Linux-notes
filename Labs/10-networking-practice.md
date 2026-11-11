# Lab 10: Networking

**Goal:** check which ports are listening on your own machine, then test the loopback address.

**Linked section:** [10-networking](../sections/10-networking.md)

## Steps

```bash
sudo ss -tulpn
ping -c 4 127.0.0.1
```

## What to check

Pick one listening port from the output and note which program owns it.

## Clean up

Nothing to clean up.

> Only scan your own machine or a lab you are allowed to test.
