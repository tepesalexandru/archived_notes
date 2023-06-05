#linux 

The `/dev` directory consists of files that represent **dev**ices that are attached to the local system. However, these are not regular files that a user can read and write to; these files are called **device files** or **special files**.

### Storage Devices
#### Block Devices
In Linux, storage devices are generally referred to as `block devices`, because data is read to and from these devices in blocks of buffered data with different sizes and positions. Every block device is identified by a file in the `/dev` directory, with the name of the file depending on the device type (IDE, SATA, SCSI, etc.) and its partitions.

#### Character Devices
A `character device` is one of the simplest wways to communicate with a module in the Linux kernel. These devices are presented as special files in the `/dev` directory and support reading and writing of any data, byte by byte, like a stream.

When calling the following command in the kernel, you get the following result:

```bash
$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 ian  8 17:31 /dev/ttyS0
```

### Major and Minor numbers
The numbers 4 and 64 are called the `Major` (4) and the `Minor` (64) numbers. Inside the Linux kernel, every device is identified not by a symbolic name but by a unique number - the device's major number.

This number is assigned by the kernel during the\ registration of the device. Every device driver can also support multiple sub-devices. 

For example, a serial port adapter may contain two hardware ports. Both of these ports are handled by the same driver, and they share one Major number. But inside this driver, each of these ports is also identified by the unique number, and this is a device Minor number.

```bash
# Same Major number (4), different Minor numbers (64-66)
crw-rw---- 1 root dialout 4, 64 Mar 11 16:52 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Mar 11 16:52 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 Mar 11 16:52 /dev/ttyS2
```
The driver's code assigns minor numbers, and the developer of this driver may select any suitable values.


Device files are an abstraction of standard devices that applications interact with via I/O system calls. These files fall into two main categories:
1. Character Special Files
2. Block Special Files

A driver communicates with a `character device` by sending single characters as data such as bytes. Example of character devices are sound cards or serial ports.

A driver communicates with a `block device` by sending an entire block of data. Example of block devices are hard disks or USBs.

Character and block devices can be identified with the `ls -l` command, by the first letter in the first column:

- b - block device
- c - character device

Example:

```bash
$ ls -l
# Character devices
crw-rw-rw-   1 root root    505,     0 ian  8 10:49 nvidia-uvm
crw-rw-rw-   1 root root    505,     1 ian  8 10:49 nvidia-uvm-tools
crw-------   1 root root    238,     0 ian  8 10:49 nvme0
# BLock devices
brw-rw----   1 root disk    259,     0 ian  8 10:49 nvme0n1
brw-rw----   1 root disk    259,     1 ian  8 10:49 nvme0n1p1
brw-rw----   1 root disk    259,     2 ian  8 10:49 nvme0n1p2
```

Other types of devices exist, such a `socket` and `pipe` devices.

### The /dev/tty file
`/dev/tty` is a special file, representing the terminal for the current process. For instance, if you execute the command:

```bash
echo 1 > /dev/tty
1
```

the output will be inside of your terminal, because `tty` IS the terminal. tty is a character special file.