# Lab 28: Disks and mounts

**Goal:** create a small disk image, format it, mount it, write to it, then unmount it. This uses a file, not a real disk, so nothing on your system is touched.

**Linked section:** [27 Disks and mounts](../sections/27-disks-and-mounts.md)

## Steps

Create a 50 MB file and format it as a file system:

```bash
mkdir -p disk-lab && cd disk-lab
truncate -s 50M lab.img
mkfs.ext4 -q -L practice lab.img
lsblk -f
```

`lsblk -f` won't show `lab.img`, because it's a file rather than a disk. That's expected.

Mount it, write a file, and check the space:

```bash
sudo mkdir -p /mnt/lab
sudo mount -o loop lab.img /mnt/lab
findmnt /mnt/lab
echo "hello disk" | sudo tee /mnt/lab/hello.txt
df -hT /mnt/lab
```

Unmount it and check that the file was saved to the image:

```bash
sudo umount /mnt/lab
sudo mount -o loop lab.img /mnt/lab
cat /mnt/lab/hello.txt
sudo umount /mnt/lab
```

## What to check

- `findmnt /mnt/lab` should show the image mounted with type `ext4`.
- `df -hT /mnt/lab` should list `ext4` and about 46 MB free.
- After remounting, `cat` should print `hello disk`. This shows the data lives on the image, not in the mount point.

## Clean up

```bash
cd ~ && rm -r disk-lab
sudo rmdir /mnt/lab
```

`rmdir` only removes `/mnt/lab` if it's empty. Make sure `sudo umount /mnt/lab` has run first, or the command will fail.
