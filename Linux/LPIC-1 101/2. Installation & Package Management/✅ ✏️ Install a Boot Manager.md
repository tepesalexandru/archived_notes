#linux #LPIC-1 

## Introduction
When a computer is powered on the first software to run is the `bootloader`. This is a piece of code whose sole purpose is to load an operating system kernel and hand over control to it. The `kernel` will load the necessary drivers, initialize the hardware and then load the rest of the operating system.

`GRUB` is the boot loader used on most Linux distributions. It can load the Linux kernel or other operating systems, such as Windows, and can handle multiple kernel images and parameters as separate menu entries.

Most Linux systems use `GRUB 2` as their default boot loader.

On systems with UEFI firmware, GRUB is loaded by the firmware from the files `grubia32.efi` (for 32-bit systems) or `grubx64.ef` (for 64-bit systems) from a partition called the `ESP` (EFI System Partition).

### MBR
`MBR` stands for `Master Boot Record`, and is a way of storing partition information on hard disks. It has its limitations, such as the inability to address disks of more than 2 TB in size, and the limit of only 4 primary partitions per disk.

### The /boot directory
On Linux the files neccesary for the boot process are usually stored on a boot partition, mounted under the root file system (`/`) and colloquially referred to as `/boot`.

Most files inside of the `/boot` directory are suffixed with the version of the Linux kernel. For example, a configuration file for the Linux kernel version `5.19.0-26-generic` will be called `config-5.19.0-26-generic`.

The `config` file, usually called `config-VERSION` (like above), stores configuration parameters for the Linux kernel. It's generated automatically and should not be directly modified by the user.

The `system map` file, usually called `System.map-VERSION`, contains a look-up table matching symbol names (like variables or functions) to their corresponding position in memory.

The `linux kernel` file, usually called `vmlinux-VERSION` or `vmlinuz` (z representing that it was compressed), contains the operating system kernel.

The `initial RAM disk` file, usually called `initrd.img-VERSION`, contains a minimal root file system loaded into a RAM disk, containing utilities and kernel modules needed so the kernel can mount the real root filesystem.

On systems with GRUB installed, you can find the GRUB config file at `/boot/grub/grub.cfg` (for GRUB 2) or `/boot/grub/menu.lst` (for GRUB Legacy). There are also `/boot/grub/i386-pc` for modules, `/boot/grub/locale` for translations and `/boot/grub/fonts` for, well, fonts.

### GRUB 2
GRUB 2 can be installed with the `grub-install` utility. 

The configuration file for GRUB 2 is `/boot/grub/grub.cfg`, and is generated automatically. It's not recommeneded to edit this file. Instead, edit the file `/etc/default/grub` and then run the `update-grub` utility to generate a compliant file.

The `update-grub` utility is a shortcut for `grub-mkconfig -o /boot/grub/grub.cfg`, so they produce the same result.

---
Concepts in this lesson:
-   ✅ `menu.lst`, `grub.cfg` and `grub.conf`
-   ✅ `grub-install`
-   ✅ `grub-mkconfig`
-   ✅ MBR

---

###  ✏️Guided Exercises
1. What is the default location for the GRUB 2 configuration file?

✅ `/boot/grub/grub.cfg`.

2. What are the steps needed to change the settings for GRUB 2?

✅ Edit the file `/etc/default/grub` and then run `update-grub`

3. Into which file should custom GRUB 2 menu entries be added?

`/etc/grub.d/40_custom`.

4. Where are the menu entries for GRUB Legacy stored?

✅ `/boot/grub/menu.lst`

5. From a GRUB 2 or GRUB Legacy menu, how can you enter the GRUB Shell?

✅ By pressing `C` in view mode, or `CTRL + C` in edit mode.
