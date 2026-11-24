# 27. Disks and mounts

A disk holds one or more **partitions**, and each partition holds a **file system**. To use a file system, Linux **mounts** it at a folder, called the mount point. Until a partition is mounted, its files can't be reached from `/`.

## Looking at disks

| Command | What it does | Example |
|---|---|---|
| `lsblk` | Lists disks and partitions as a tree | `lsblk` |
| `lsblk -f` | Adds the file system type, label, and UUID | `lsblk -f` |
| `sudo blkid` | Shows the UUID and type of each partition | `sudo blkid` |
| `df -hT` | Shows mounted file systems with their type and free space | `df -hT` |
| `findmnt` | Shows the mounted file systems as a tree | `findmnt` |
| `dmesg \| tail` | Shows kernel messages, useful after plugging in a USB drive | `sudo dmesg \| tail` |

Use `lsblk -f` to find the device name before you mount anything. Device names such as `sdb1` can change between boots, so the UUID is more reliable for permanent mounts.

## Mounting and unmounting

| Command | What it does | Example |
|---|---|---|
| `sudo mkdir -p /mnt/usb` | Creates a mount point | `sudo mkdir -p /mnt/usb` |
| `sudo mount /dev/sdb1 /mnt/usb` | Mounts a partition at the mount point | `sudo mount /dev/sdb1 /mnt/usb` |
| `sudo mount` | Lists everything currently mounted | `sudo mount` |
| `sudo umount /mnt/usb` | Unmounts it. Do this before unplugging | `sudo umount /mnt/usb` |

`umount` fails with "target is busy" if a program has a file open or your shell is inside the folder. Run `cd ~` and try again.

## Mounting at boot with /etc/fstab

`/etc/fstab` lists the file systems to mount automatically. Each line has six fields:

```
UUID=1234-ABCD  /mnt/data  ext4  defaults  0  2
```

| Field | Meaning |
|---|---|
| Device | A UUID, label, or device path |
| Mount point | Where it appears |
| Type | The file system, such as `ext4`, `vfat`, or `ntfs` |
| Options | Settings such as `defaults` or `ro` for read-only |
| Dump | Usually `0` |
| Pass | Check order at boot: `0` skips the check, `1` is the root file system, `2` is everything else |

Before editing `/etc/fstab`:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

After editing, test without rebooting:

```bash
sudo mount -a
findmnt /mnt/data
```

> A wrong line in `/etc/fstab` can stop the system from booting. Always keep the backup, and test with `sudo mount -a` before you reboot.

## Formatting a disk

Formatting erases everything on the partition. Only do it on an empty spare disk or a file you created for practice.

```bash
sudo mkfs.ext4 -L practice /dev/sdX1
```

Replace `/dev/sdX1` with your device. Check it twice with `lsblk -f` first.

## Notes

- Check the device name with `lsblk` before every mount, because a wrong name can point at your system disk.
- Use `sync` or `umount` before you remove a USB drive, so writes finish.
- Filesystem types: `ext4` for Linux, `vfat` for simple shared drives, and `ntfs` for Windows drives.

## Practice

Try the hands-on lab for this section: [Labs/28-disks-practice.md](../Labs/28-disks-practice.md)
