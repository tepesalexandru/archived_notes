#linux #LPIC-1 

## Introduction
On any operating system, a disk needs to be partitioned before it can be used. A partition is a logical subset of the physical disk, and information about partitions are stored in a partition table. This table includes information about the first and last sectors of the partition and its type, and further details on each partition.

On Windows systems, they are assigned letters like `C:`, `D:` and so on. On Linux however, each partition is assigned to a directory under `/dev`, such as `/dev/sda1` or `/dev/sda2`.

## Understanding MBR and GPT
There are two main ways of storing aprtition information on hard disks. The first one is `MBR` (Master Boot Record), and the second one `GPT` (GUID Partition Table).

### MBR
The partition table is stored on the first sector of a disk, called the `Boot Sector`, along with a boot loader, which on Linux systems is usually the GRUB bootloader.

MBR has its limitations, such as having a maximum disk size of 2 TB and only 4 primary partitions per disk.

### GUID
This partitioning system addresses the limitations of MBR. There is no practical limit on disk size, and the maximum number of partitions are limited only by the operating system iteself. It's commonly found in machines that use UEFI instead of the old PC BIOS.

## Managing MBR Partitions with FDISK
The standard utility for managing MBR partitions on Linux is `fdisk`. This is an interactive, menu-driven utility. In order to use it, type `fdisk` followed by the device name corresponding to the disk you want to edit.

```shell
$ fdisk /dev/sda
```

### Primary vs Extended Partitions
On an MBR disk, you can have 2 main types of partitions, `primary` and `extended`. Like we said before, you can only have 4 primary partitions on the disk, and if you want to make the disk "bootable", the first partition must be a primary one.

One way to work around this limitation is to create an *extended partition* that acts as a container for logical partitions. For example, you could have a primary partition and an extended partition occupying the remainder of the disk space, containing five logical partitions inside of it.

When using Linux, primary and extended partitions are treated exactly in the same way, so there is no "advantage" of using one over the other.

### Creating a Partition
In order to create a partition, use the `n` command. By default, partitions will be created at the start of unallocated space on the disk. You will be asked for the partition type (`primary` or `extended`), first sector and last sector.

The following series of commands will create a 1 GB size partition.

```shell
Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-3903577, default 2048): 2048
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-3903577, default 3903577): +1G
```

## Managing GUID Partitions with GDISK
The utility `gdisk` is the equivalent of `fdisk` when dealing with GPT partitioned disks. In fact, the interface is modeled after `fdisk`, with an interactive prompt and the same (or very similar) commands.

## Creating File Systems
Partitioning the disk is only the first step towards being able to use the disk. *After* that, you will need to format the partition with a filesystem before using it to store data.

A `filesystem` controls how the data is stored and accessed on the disk. Linux supports many filesystems, some native, like the `ext` (Extended Filesystem) family, while others come from other operating systems like FAT from MS-DOS, NTFS from Windows NT, HFS and HFS+ from Mac OS, etc.

The standard tool used to create a filesystem on linux is `mkfs`, which comes in many "flavors" according to the filesystem it needs to work with.

## Creating an ext2/ext3/ext4 Filesystem
The *Extended Filesystem* (ext) was the first filesystem for Linux, and through the years was replaced by new versions called `ext2`, `ext3`, and `ext4`, which is currently the default filesystem for many Linux distributions.

The utilities `mkfs.ext2`, `mkfs.ext3`, and `mkfs.ext4` are used to create ext2, ext3, and ext4 filesystems.

In fact, all of these "utilities" exist only as `symbolic links` to another utility called `mke2fs`.

`mke2fs` alters its defaults according to the name it is called by. As such, they all have the same behaviour and command line patterns.

The most simple form of usage of the `mkfs` command is the following:

```shell
$ mkfs.ext2 TARGET
```

Where `TARGET` is the name of the partition where the filesystem should be created. For example, to create an ext3 filesystem on `/dev/sdb1` the command would be:

```shell
$ mkfs.ext3 /dev/sdb1
```

Or, instead of using the command corresponding to the filesystem you with to create, you can pass the `-t` parameter to `mke2fs` followed by the filesystem name. As an example, the following two commands are equivalent:

```shell
$ mkfs.ext4 /dev/sdb1
$ mke2fs -t ext4 /dev/sdb1
```

## Creating an XFS Filesystem
XFS is a high-performance filesystem originally developed by Silicon Graphics in 1993 for its IRIX operating system. Due to its performance and reliability features, it is commonly used for servers and other environments that require high (or guaranteed) filesystem bandwidth.

Tools for managing XFS filesystems are part of the `xfsprogs` package. This package may need to be installed manually, as it is not included by default in some Linux distributions.

XFS filesystems are divided into at least 2 parts: a `log section` and a `data section`.

The log section may be located inside the data section (the default behaviour), or even on a separate disk altogether, for better performance and reliability.

The most basic command to create an XFS filesystem is `mkfs.xfs TARGET`, where TARGET is the partition you want the filesystem to be created on. For example:

```shell
$ mkfs.xfs /dev/sda1
```

## Managing Partitions with GNU Parted
*GNU Parted* is a very powerful partition editor that can be used to create, delete, move, resize, rescue, and copy partitions. It can work both with `GPT` and `MBR` disks, and cover almost all of your disk management needs.

There are many graphical front-ends that make working with `parted` much easier, like *GParted* for GNOME-based desktop environments, and the *KDE Partition Manager* for KDE Desktops.

The simplest way to start using parted is by typing `parted DEVICE`, where DEVICE is the device you want to manage. The program starts an interactive command line interface like `fdisk` and `gdisk`. An example:

```shell
$ parted /dev/sdb 
# Or
$ parted # Selects the default disk
```

### Selecting Disks
To switch to a different disk than the one specified on the command line, you can use the `select` command, followed by the device name:

```shell
$ (parted) select /dev/sdb

Using /dev/sdb
```

### Getting Information
The `print` command can  be used to get more information about a specific partition or even all of the block devices (disks) connected to your system. An example:

```shell
$ (parted) print

Model: Virtio Block Device (virtblk)
Disk /dev/vda: 10.7GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
14      1049kB  5243kB  4194kB                     bios_grub
15      5243kB  116MB   111MB   fat32              boot, esp
 1      116MB   10.7GB  10.6GB  ext4
```

You can get a list of all block devices connected to your system using `print devices`:

```shell
$ (parted) print devices

/dev/sdb (1999MB)
/dev/sda (120GB)
/dev/sdc (320GB)
/dev/mapper/cryptswap (4294MB)
```

### Creating a Partition Table on an Empty Disk
To create a partition on an empty disk, use the `mklabel` command, followed by the partition table type that you want to use.

There are many supported table types, but the main types you should know of are `msdos`, which is used to refer to an MBR partition table, and `gpt` to refer to a GPT partition table. As an example:

```shell
$ (parted) mklabel msdos # Creates an MBR partition table
$ (parted) mklabel gpt # Creates a GPT partition table
```

### Create a Partition
To create a partition, the command `mkpart` is used, using the syntax:

```shell
$ (parted) mkpart PARTTYPE FSTYPE START END
```

- PARTTYPE - the partition type, can be `primary`, `logical`, or `extended` in case an MBR partition table is used.
- FSTYPE - the filesystem type on this partition. `parted` does *not* create the filesystem, it only sets a flag on the partition which tells the OS what kind of data to expect from it.
- START - specifies the exact point on the device where the partition begins.
- END - specifies the end of the partition

Therefore, the following command:

```shell
$ (parted) mkpart primary ext4 1m 100m
```

Creates a primary partition of type ext4, starting at the first megabyte of the disk, and ending after the 100th megabyte.

### Creating Swap Partitions
On Linux, the system can swap memory pages from RAM to disk as needed, storing them on a separate space usually implemented as a separate partition on a disk, called the `swap partition` or simply `swap`.

This partition needs to be of a specific type, and set-up with a proper utility (`mkswap`) before it can be used.

---

Concepts in this lesson:
-   ✅ `fdisk`
-   ✅ `gdisk`
-   ✅ `parted`
-   ✅ `mkfs`
-   ✅ `mkswap`
