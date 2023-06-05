#linux #LPIC-1 

## Introduction
In order to control the machine, the operating system's main component - the kernel - must be loaded by a program called a `bootloader`, which itself is loaded by a pre-installed firmware such as BIOS or UEFI.

The first 512 bytes of a storage device are named the `MBR` (Master Boot Directory).

On a machine equipped with a BIOS firmware, the `bootstrap` binary is located in the MBR of the first storage device.

UEFI, short for *Unified Extensible FIrmware Interface*, does not rely on the MBR, taking into account only the settings stored in its non-volatile memory (*NVRAM*) attached to the motherboard.

These definitions indicate the location of the UEFI compatible programs, called *EFI applications*, that will be executed automatically or called from a boot menu.

EFI applications can be bootloaders, operating system selectors, tools for system diagnostics and repair, etc.

## The Bootloader
The most popular bootloader for Linux in the x86 architecture is GRUB (Grand Unified Bootloader).

From the GRUB menu it is possible to choose which one of the installed kernels should be loaded and to pass new parameters to it.

Some of the most useful kernel parameters are:
- `init` - sets an alternative system initiator. For example:

```shell
$ init=/bin/bash # This will Bash as the initiator
```

The above command will start a shell session just after the kernel boot process.

## System Initialization
Apart from the kernel, the operating system depends on other components that provide the expected features. Many of these components are loaded during the system initialization process, varying from simple `shell scripts` to more complex `service programs`.

Scripts are often used to perform short lived tasks that will run and terminate during the system initialization process.

Services, also known as `daemons`, may be active all the time as they can be responsible for instrisic aspects of the operating system.

The initialization of the operating system starts when the bootloader loads the kernel into RAM, after which the kernel will take charge of the CPU.

The kernel will then open the `initramfs` (initial RAM filesystem). The initramfs is an archive containing a filesystem used as a temporary root filesystem during the boot process. The main purpose of an initramfs file is to provide the required modules so the kernel can acess the "real" root filesystem of the operating system.

### SysV standard
A service manager based on the `SysVinit` standard controls which daemons and resources will be available by employing the concept of `runlevels`. Runlevels are numbered 0 to 6 and are designed by the distribution maintainers to fulfill specific purposes. The only runlevel definitions shared between all distributions are the runlevels 0, 1, and 6.

### systemd
`systemd` is a modern system and services manager with a compatibility layer for the `SysV` commands and runlevels. systemd has a concurrent structure, employs sockets and D-Bus for service activation, on-demand daemon execution, process monitoring with `cgroups`, snapshot support, system session recovery, mount point control and a dependency-based service control. 

In recent years most major Linux distributions have gradually adopted systemd as their default system manager.

## Initialization Inspection
Errors may occur during the boot process, but they may not be so critical to completely halt the operating system.

The memory space where the kernel stores its messages, including the boot messages, is called the `kernel ring buffer`. The messages are kept in the kernel ring buffer even when they are not displayed during the initialization process, like when an animation is displayed instead.

However, the kernel ring buffer loses all messages when the system is turned off or by executing the command:

```shell
$ dmesg --clear # Clears the kernel ring buffer messages
```

Without any options, the `dmesg` command displays all the current messages in the krnel ring buffer (can be hundreds of lines):

```shell
$ dmesg # Shows all the current messages in the kernel buffer ring
```

In systems based on systemd, command `journalctl` will show the initialization messages with options `-b`, `--boot`, `-k` or `--dmesg`.

The following command will show a list of boot numbers relative to the current boot:

```shell
$ journalctl --list-boots

# Sample output:
-4 9e5b3eb4952845208b841ad4dbefa1a6 Thu 2019-10-03 13:39:23 -03—Thu 2019-10-03 13:40:30 -03
 -3 9e3d79955535430aa43baa17758f40fa Thu 2019-10-03 13:41:15 -03—Thu 2019-10-03 14:56:19 -03
 -2 17672d8851694e6c9bb102df7355452c Thu 2019-10-03 14:56:57 -03—Thu 2019-10-03 19:27:16 -03
 -1 55c0d9439bfb4e85a20a62776d0dbb4d Thu 2019-10-03 19:27:53 -03—Fri 2019-10-04 00:28:47 -03
  0 08fbbebd9f964a74b8a02bb27b200622 Fri 2019-10-04 00:31:01 -03—Fri 2019-10-04 10:17:01 -03
```

In order to view the initialization logs of a specific boot, you can use the `journalctl -b` command, using the relative boot number as parameter:

```shell
$ journalctl -b 0 # This will show the current initialization logs
```

Initialization and other messages issued by the operating system are stored in files inside the directory `/var/log`. The log messages are not stored in raw text, they need to be read using the `journalctl` command.

---

Concepts in this lesson:
-   ✅ `dmesg`
-   ✅ `journalctl`
-   ✅ BIOS 
-   ✅ UEFI 
-   ✅ bootloader
-   ✅ kernel 
-   ✅ `initramfs`
-   ✅ `init`
-   ✅ SysVinit
-   ✅ systemd

---

###  ✏️ Guided Exercises
1. On a machine equipped with BIOS firmware, where is the boostrap binary located?

✅ In the Master Boot Directory of the first storage device.

2. UEFI firmware supports extended features provied by external programs, called EFI applications. These applications, however, have their own special location. Where on the system would the EFI applications be located?

✅ In the EFI System Partition (ESP) in a compatible filesystem (FAT12, FAT16 and FAT32 for block devices and ISO-9660 for optical media).

3. Bootloaders allow the passing of custom kernel parameters before loading it. Suppose the system is unable to boot due to misinformed root filesystem location. How would the correct root filesystem, located at `/dev/sda3`, be given as a parameter to the kernel?

✅ The `root` parameter should be used, `root=/dev/sda3`.

4. The boot process of a Linux machine ends up with the following message:
```bash
ALERT! /dev/sda3 does not exist. Dropping to a shell!
```
What is the likely cause of this problem?

✅ The kernel was unable to find the device `/dev/sda3`, informed as the root filesystem.