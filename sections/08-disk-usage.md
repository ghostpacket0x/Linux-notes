# 8. Disk usage

Two questions come up often: "how big is this folder?" and "how much space is left?"

## Quick reference

| Command | What it does |
|---|---|
| `du` | Estimates the space a folder uses |
| `df` | Shows free space on mounted disks |
| `free` | Shows memory (RAM) and swap usage |
| `mount` | Attaches a device or file system to a folder |
| `umount` | Detaches a mounted device |
| `eject` | Ejects removable media |
| `sync` | Writes cached data to disk |
| `fsck` | Checks and repairs a file system |
| `fdisk` | Partition table manipulator |
| `mkfs` | Creates a file system on a device |
| `quota` | Shows disk usage and limits |
| `quotacheck` | Scans a file system to update quota information |
| `setquota` | Sets disk quota limits for a user or group |

## Disk usage

| Command | What it does | Example |
|---|---|---|
| `du` | Shows the space each folder uses, in raw blocks | `du` |
| `du -h` | The same, in an easy-to-read form | `du -h` |
| `du -sh <folder>` | A single total for one folder (`s` = summary) | `du -sh Documents` |
| `df` | Shows free space on each disk | `df` |
| `df -h` | The same, in an easy-to-read form | `df -h` |
| `free` | Shows memory (RAM) and swap usage | `free -h` |

## More disk commands

| Command | What it does | Example |
|---|---|---|
| `mount` | Shows mounted devices, or attaches one to a folder (needs root to attach) | `sudo mount /dev/sdb1 /mnt/usb` |
| `umount <mountpoint>` | Detaches a mounted device | `sudo umount /mnt/usb` |
| `eject <device>` | Ejects removable media | `eject /dev/sr0` |
| `sync` | Writes cached data to disk | `sync` |
| `fsck <device>` | Checks and repairs a file system. Run it on an unmounted disk | `sudo fsck /dev/sdb1` |
| `fdisk -l` | Partition table manipulator. The `-l` option lists disks and partitions | `sudo fdisk -l` |
| `mkfs` | Creates a file system on a device | `sudo mkfs.ext4 /dev/sdb1` |
| `quota` | Shows disk usage and limits for a user | `quota` |
| `quotacheck` | Scans a file system to update disk quota information | `sudo quotacheck -cu /home` |
| `setquota` | Sets disk quota limits for a user or group | `sudo setquota -u alice 1000 2000 0 0 /home` |

## Practice 

Try the hands-on lab for this section: [Labs/08-disk-practice.md](../Labs/08-disk-practice.md)
