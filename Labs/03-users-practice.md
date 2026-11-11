# Lab 03: Users and groups

**Goal:** create a test user, check its details, then remove it.

**Linked section:** [03 Users and groups](../sections/03-users-and-groups.md)

## Steps

```bash
sudo adduser practice_user
id practice_user
getent passwd practice_user
sudo deluser --remove-home practice_user
getent passwd practice_user
```

## What to check

The last `getent` should print nothing, which shows the account has gone.

## Clean up

Use this lab only on your own VM with a test account. The `deluser` line removes the user and its home folder.
