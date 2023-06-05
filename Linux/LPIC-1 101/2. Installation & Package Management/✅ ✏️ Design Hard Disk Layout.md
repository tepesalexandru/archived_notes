#linux #LPIC-1 

## Introduction
Think of a `disk` (or storage device, since modern devices do not contain any "disks" at all) as a "physical container" for your data.

Before a disk can be used by a computer it needs to be `partitioned`. A partition is a logical subset of the physical disk.

Partitioning is a way to "compartmentalize" information stored on the disk, separating, for example, operating system data from user data.

Inside each partition there is a `filesystem`. The filesystem describes the way the information is actually stored on the tisk. This information includes how the directories are organized, what is the relationship between them, where is the data for each file, etc.

## Mount Points
Before a filesystem can be accessed on Linux it needs to be *mounted*. This means attaching the filesystem to a specific point in your system's directory tree, called a *mount point*.

When mounted, the contents of the filesystem will be available under the mount point. For example, imagine you have a partition with your users' personal data, containing the directories `/john` , `/jack`, and `/carol`.

When mounted under `/home`, the contents of those directories will be available under `/home/john`, `/jack` and `/carol`.

The default mount point for any user-removable media is `/media` (e.g. external disks, USB flash drives, memory card readers, optical disks, etc.)

On most modern Linux distributions and desktop environments, removable devices are automatically mounted under `/media/USER/LABEL`, where USER is the username and LABEL is the device label (e.g. `/media/john/FlashDrive/`).

## The Boot Partition
The boot partition contains files used by the bootloader to load the operating system. On Linux systems, the bootloader is usually GRUB2 (or GRUB Legacy for older systems), and is mounted under `/boot` and its files are stored in `/boot/grub`.

## The EFI System Partition (ESP)
The *EFI System Partition* (ESP) is used by machines based on the UEFI to store boot loaders and kernel images for the operating system.

On machines running Microsoft Windows this partition is usually the first one on the disk, although this is not required. The ESP is created (or populated) by the operating system upon installation, and on a Linux system is mounted under `/boot/efi`.

## The /home Partition
Each user in the system has a home directory to store personal files and preferences, and most of them are located under `/home`. Usually the home directory is the same as the username, so the user John would have his directory under `/home/john`.

There are expections however. For example the home directory for the root user is `/root` and some systems may have associated users with home directories elsewhere.

## Variable Data (/var)
This sytem directory contains "variably data", or files and directories the system must be able to write to during operation. This includes:
- System Logs (`/var/log`)
- Temporary files (`/var/tmp`)
- Cached application data (`/var/cache`)

## Swap
The swap partition is used to swap memory pages from RAM to disk as needed. This partition needs to be of a specific type, and set-up with proper utility called `mkswap` before it can be used.

This swap partition cannot be mounted like the others, meaning that you cannot access it like a normal directory and peek its contents.

## LVM
`Logical Volume Managemenet` (LVM) is a form of storage virtualization that offers system administrators a more flexible approach to managing disk space than traditional partitioning. The goal of LVM is to facilitate managing the storage needs of your end users.

The basic unit is the `Physical Volume` (PV), which is a block device on your system like a disk partition or a RAID array.

PVs are grouped into `Volume Groups` (VG) which abstract the underlying devices and are seen as a single logical device, with the combined storage capabity of the component PVs.

---
Concepts in this lesson:
-   ✅ `/` (root) filesystem
-   ✅ `/var` filesystem
-   ✅ `/home` filesystem
-   ✅ `/boot` filesystem
-   ✅ EFI System Partition (ESP)
-   ✅ swap space
-   ✅ mount points
-   ✅ partitions

---

###  ✏️ Guided Exercises
1. On Linux systems, where are the files for the GRUB bootloader stored?

✅ In the `/boot/grub` directory.

2. Where should the boot partition end to ensure that a PC will always be able to load the kernel?

✅ The boot partition is usually located at the start of the disk and ends before cylinder 1024 (528 MB).

3. Where is the EFI partition usually mounted?

✅ In the `/boot/efi` directory.

4. When manually mounting a filesystem, under which directory should it usually be mounted?

✅ In the `/mnt` directory.