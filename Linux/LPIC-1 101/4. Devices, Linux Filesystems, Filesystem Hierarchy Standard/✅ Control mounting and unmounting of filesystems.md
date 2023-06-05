#linux #LPIC-1 

### Mounting and Unmounting
Before a filesystem can be accessed on Linux, it first needs to be *mounted*.

The act of *mounting* means attaching the filesystem to a specific point in your system's directory tree, called a *mount point*.

You can mount a filesystem manually with the `mount` command:

```bash
mount -t TYPE DEVICE MOUNTPOINT
```
By typing just `mount`, you will get a list of all filesystems currently mounted on your system.

You can filter the list by only showing a specific type using `-t`:

```bash
mount -t ext4 # Only shows ext4 filesystems
mount -t ext3,ext4 # Only shows ext3 and ext4 filesystems
```

To unmount a filesystem, use the `unmount` command, followed by the device name or the mount point:

```bash
unmount /dev/sdb1
```
When unmounting a filesystem, you will get an error if a file in that current filesystem is open. Since its hard to guess which file is open, you can use the `lsof` command to find that out:

```bash
lsof /dev/sdb1 # Shows all open files inside the /dev/sdb1 filesystem
```
To make system administration easier, the `/media` directory has become the default mount point for any user-removable media (e.g. external disks, USB flash drives, memory card readers, etc.) connected to the system.

However, if you need to manually mount a filesystem, it is good practice to mount it under `/mnt`.

### Other
The file `/etc/fstab` contains descriptions about the filesystems that can be mounted.

The command `lsblk` can be used to query information about a filesystem and find out the label and UUID associated to it.

```bash
lsblk -f /dev/nvme0n1p1
NAME      FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
nvme0n1p1 vfat   FAT32       031A-3928                             504,9M     1% /boot/efi

```
`Systemd` is the init process, the first process to run on many Linux distributions. Among many other tasks, `systemd` can also be used to manage the mounting and automounting of filesystems.

To use this feature, you need to create a configuration file called a *mount unit*. Each volume to be mounted gets its own mount unit and they ened ot be placed in `/etc/systemd/system`.

---

Key knowledge areas
• Manually mount and unmount filesystems.
• Configure filesystem mounting on bootup.
• Configure user mountable removable filesystems.
• Use of labels and UUIDs for identifying and mounting file systems.
• Awareness of systemd mount units.

Partial list of the used files, terms and utilities
- ✅ `/etc/fstab`
- ✅ `/media/`
- ✅ `mount`
- ✅ `umount`
- ✅ `blkid` (?)
- ✅ `lsblk`