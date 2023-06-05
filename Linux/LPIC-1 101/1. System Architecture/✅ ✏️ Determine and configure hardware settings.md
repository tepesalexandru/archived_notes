#linux #LPIC-1 

## Introduction
Most machines offer a configuration utility that can be executed as the machine is turned on. Until the mid 2000s, the configuration utility was implemented in the `BIOS` (Basic Input/Output System), found in x86 motherboards.

From the end of first decade of the 2000s, a new implementation called `UEFI` (Unified Extensible Firmware Interface) started replacing the BIOS, but its not uncommon to still call it BIOS, as it servers the same purpose.

## Device Activation
Usually, you can enter the BIOS by pressing a specific key when the computer is turned on. Which key to press varies from manufacturer to manufacturer, but its usually `Del`, `F2`, or `F12`.

If the machine is equipped with many storage devices, it is important to define which one has the correct bootloader and should be the first entry in the device boot order. The operating system may not load if the incorrect device comes first in the BIOS boot verification list.

## Commands for Inspection
There are two essential commands to identify connected devices in a Linux system:

- `lspci` - Shows all devices currently connected to the `PCI` (Peripheral Component Interconnect) bus. 

PCI devices can be either a component attached to the motherboard, like a disk controller, or an expansion card fitted into a PCI slot, like an external graphics card.

- `lsusb` - Lists USB (Universal Serial Bus) devices currently connected to the machine.

The USB interface is usually used to connect input devices, such as keyboard and pointing devices, and removable storage media.

The output of the `lspci` and `lsusb` commands consist of a list of all PCI and USB devices identified by the operating system. However, the device may not be fully operational yet, because every hardware part requires a software component to control the corresponding device.

This software component is called a `kernel module` and it can be part of the official Linux kernel or added separately from other sources.

Linux kernel modules related to hardware devices are also called `drivers`, as in other operating systems. 

Commands directly related to hardware often required `root privileges` to executre or will only show limited information when executed by a normal user, so it may be necessary to login as root ro to execute the command with `sudo`.

You can get additional information about a PCI component by using the command

```bash
$ lspci -s <hex-address> -v # example HEX Address: 04:02.0
```

You can also view the current kernel drivers mounted either with the command above, which is more verbose, or with the following command:

```shell
$ lspci -s <hex-address> -k # This will output the kernel driver in use
```

If the kernel driver is correctly mounted, it can be assumed that the device is ready to use.

It is a common practice to use commands provided by the `kmod` package in order to handle common tasks with Linux kernel modules like insert, remove, list, check properties, resolve dependencies and aliases.

An example command from the kmod package is `lsmod`, which will show all currently loaded modules. The output of this command contains three columns:
- Module - the module's name
- Size - the amount of RAM occupied by the module, in bytes
- Used by - a list of depending modules

The command `modprobe` can be used to both load and unload kernel modules. You are allowed to remove a kernel module as long as no running process is using it.

```shell
$ modprobe -r snd-hda-intel # Will remove the snd-hda-intel kernel module
```

## Information Files and Device Files
The commands `lspci`, `lsusb` and `lsmod` act as front-ends to real hardware information stored by the operating system.

This kind of information is kept in special files in the directories `/proc` and `/sys`. These directories are mount points to filesystems not present in a device partition, but only in RAM space used by the kernel to store runtime configuration and information on running processes.

These are called *pseudo-filesystems* and only exist while the system is running.

The `/proc` directory contains files with information regarding running processes and hardware resources.

The `/sys` directory has the specific purpose of storing device information and kernel data related to hardware.

## Storage Devices
In Linux, storage devices are generally referred as *block devices*, because data is read to and from these devices in blocks of buffered data with different sizes and positions. 

Every block device is identified by a file in the `/dev` directory, with the name of the file depending on the device type (IDE, SATA, SCSI, etc.)

---

Concepts in this lesson:
-   ✅ `/sys/` 
-   ✅ `/proc/`
-   ✅ `/dev/`
-   ✅ `modprobe`
-   ✅ `lsmod`
-   ✅ `lspci`
-   ✅ `lsusb`

---

###  ✏️ Guided Exercises
1. Suppose an operating system is unable to boot after adding a second SATA disk to the system. Knowing that all parts are not defective, what could be the possible cause for this error?

✅ The incorrect device is first in the BIOS boot verification list.

2. Suppose you want to make sure the external video card connected to the PCI bus of your newly aquired desktop computer really is the one advertised by the manufacturer, but opening the computer case will void the warranty. What command could be used to list the details of the video card, as they were detected by the operating system?

✅ By using the `lspci` command.


3. The following line is part of the output generated by the command `lspci`:
```bash
03:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 2208
[Thunderbolt] (rev 05)
```
What command should you execute to identify the kernel module in use for this specific device?

✅ By using the command `lspci -s 03:00.0 -k`.

4. A system administrator wants to try different parameters for the `bluetooth` kernel module without rebooting the system. However, any attempt to unload the module with `modprobe -r bluetooth` results in the following error:
```bash
modprobe: FATAL: Module bluetooth is in use.
```
What is the possible cause for this error?

✅ A running process is using the `bluetooth` module.

