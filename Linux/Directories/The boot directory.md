#linux 

Every Linux system has a boot directory, with all the needed files for the boot process. This directory is mounted directly on the root file system and is called **/boot**.

On my Linux system (Ubuntu 22.10), when I go into the /boot directory and call the **ls** utility, I get the following result:

```bash
$ cd /boot  
$ ls  
config-5.19.0-26-generic      memtest86+.elf  
config-5.19.0-28-generic      memtest86+_multiboot.bin  
efi                           System.map-5.19.0-26-generic  
grub                          System.map-5.19.0-28-generic  
initrd.img                    vmlinuz  
initrd.img-5.19.0-26-generic  vmlinuz-5.19.0-26-generic  
initrd.img-5.19.0-28-generic  vmlinuz-5.19.0-28-generic  
initrd.img.old                vmlinuz.old
```

Out of all of these files, there are four that stand out:

1.  The **Configuration** file
2.  The **System Map** file
3.  The **Linux Kernel** file
4.  The **Initial RAM Disk** file

I’d like to dive into what these files represent, and for that, it’s important to notice that all of them have a suffix. The suffix represents the Linux Kernel version that they target.

For instance, if the target version is “**5.19.0–26-generic**”, then the name of the configuration file will be “**config-5.19.0–26-generic**”.

## The Configuration File

The configuration file is usually noted as “**config-VERSION**” and contains the configuration parameters for the Linux Kernel (VERSION being a placeholder for the Linux Kernel Version).

This file is generated automatically, and it’s advised not to modify it directly.

If you’re curious about what the inside of the file looks like, here you go:

```bash
$ cat config-5.19.0-26-generic  
#  
# x86 Debugging  
#  
CONFIG_EARLY_PRINTK_USB=y  
# CONFIG_X86_VERBOSE_BOOTUP is not set  
CONFIG_EARLY_PRINTK=y  
CONFIG_EARLY_PRINTK_DBGP=y  
CONFIG_EARLY_PRINTK_USB_XDBC=y  
# CONFIG_EFI_PGT_DUMP is not set  
# CONFIG_DEBUG_TLBFLUSH is not set  
# CONFIG_IOMMU_DEBUG is not set  
CONFIG_HAVE_MMIOTRACE_SUPPORT=y  
# CONFIG_X86_DECODER_SELFTEST is not set  
# CONFIG_IO_DELAY_0X80 is not set  
CONFIG_IO_DELAY_0XED=y  
...
```

## The System Map File

The System Map is a look-up table matching variables and functions to their corresponding position in memory.

The file name is usually called “**System.map-VERSION**”, and its contents can be seen with superuser (**sudo**) privileges :

```bash
$ sudo cat System.map-5.19.0-26-generic  
ffffffff8399b580 b __key.0  
ffffffff8399b580 b scsi_dev_flags  
ffffffff8399b680 b scsi_default_dev_flags  
ffffffff8399b688 B scsi_nl_sock  
ffffffff8399b690 b scsi_table_header  
ffffffff8399b698 b proc_scsi  
ffffffff8399b6a0 b list_lock  
ffffffff8399b6a8 b __key.0  
ffffffff8399b6a8 b sd_bio_compl_lkclass  
ffffffff8399b6a8 b sd_page_pool  
ffffffff8399b6b0 b sd_cdb_cache  
ffffffff8399b6b8 b __key.0  
ffffffff8399b6c0 b __key.1  
...
```

## The Linux Kernel File

This file contains the operating system kernel, and is stored in a file called “**vmlinux-VERSION**”.

Sometimes, this file is also called “**vmlinuz-VERSION**” (with a z instead of an x), representing that it has been compressed.

Since my kernel file is compressed, using the cat command only spits out random symbols into the console, so it’s not worth showing.

## The Initial RAM Disk

Last, but not least important is the “**initrd.img-VERSION**” file.

The primary function of this file is to load a minimal root file system into RAM, containing all the utilities and kernel modules needed to load the actual root file system.

Same as the last file, this is also encrypted and the cat command is not that useful.