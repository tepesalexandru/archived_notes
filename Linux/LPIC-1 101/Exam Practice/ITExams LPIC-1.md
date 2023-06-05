#linux #LPIC-1 

1. Instead of supplying an explicit device in `/etc/fstab` for mounting, what other options may be used to identify the intended partition?

Answer: `LABEL` and `NAME`

2. A yum repository can declare sets of related packages. Which yum command installs all the packages belonging to the group admintools?

Answer: `yum groupinstall admintools`

3. What directory contains configuration files for additional yum repositories?

Answer: `/etc/yum.conf`

4. Which of the following commands installs the GRUB boot files into the currently active file systems and the boot loader into the first partition of the first disk?

Answer: `grub-install /dev/sda` 

5. Which of the following files are found in the `/boot/` file system?

Answer: `Linux kernel images` and `systemd target and service units`.

6. Which file defines the network locations from where the Debian package manager downloads software packages?

Answer: `/etc/apt/sources.list`

7. When removing a package on a system using `dpkg` package management, which dpkg option ensures configuration files are removed as well?

Answer: `--purge`

8. Which of the following statements are correct when comparing Linux containers with traditional virtual machines?

Answers: 
- Containers are a lightweight virtualization method where the kernel controls process isolation and resource management
- Fully virtualized machines can run any operating system for a specific hardware architecture within the virtual machine
- The guest environment for fully virtualized machines is created by a hypervisor which provides virtual and emulated hardware devices.

9. The installation of a local Debian package failed due to unsatisfied dependencies. Which of the following commands installs missing dependencies and completes the interrupted package installation?

Answer: `apt-get install -f`

10. Which of the following commands lists all currently installed packages when using RPM package management?

Answer: `rpm --query --all`

11. Which of the following commands are valid in the GRUB 2 configuration file?

Answer: `menuentry` and `insmod`

12. What is the purpose of the `ldd` command?

Answer: It lists which shared libraries a binary needs to run.

13. What can the `Logical Volume Manager` (LVM) be used for?

Answers:
- To create snapshots
- To dynamically change the size of logical volumes
- To dynamically create or delete logical volumes

14. What are the main differences between `GPT` and `MBR` partition tables ragarding maximum number and size of partitions?

Answers:
- By default, GPT can manage up to 128 partitions while MBR only supports 4 primary partitions
- MBR can handle partition sizes up to 2.2 TB, whereas GPT supports sizes up to 9.4 ZB

15. A backup software heavily uses hard links between files which have not been changes in between two backup runs. Which benefits are realized due to these hard links?

Answers:
- The old backups can be moved to slow backup media, such as tapes, while still serving as hard link target in new backups
- The backup consumes less space because the hard links point to the same data on disk instead of storing redundant copies

---

## Topic 1
1. Which type of file system is created by `mkfs` when it is executed with the block device name only and without any additional parameters?

Answer: ext2

2. Which `umask` value ensures that new directories can be read, written and listed by their owning user, read and listed by their owning group and are not accessible at all for everyone else?

Answer: 0027

3. Which command changes the number of days before the ext3 filesystem on `/dev/sda1` has to run through a full system check while booting?

Answer: `tune2fs -i 200 /dev/sda1`

4. Which is the default percentage of reserved space for the root user on new ext4 filesystems?

Answer: `5%`

5. Which of the following is true when a file system, which is neither listed in `/etc/fstab` nor known to system, is mounted manually?

Answer: `systemd` automatically generated a mount unit and monitors the mount point without changing it.

6. Which program updates the database that is used by the locate command?

Answer: `updatedb`

7. What does the command `mount -bind` do?

Answer: It makes the contents of one directory available in another directory.

8. Weird text
9. Weird text

10. In order to display all currently mounted filsystems, which of the following commands could be used?

Answer:
- `cat /proc/self/mounts`
- `cat /proc/filesystems`

11. Which command displays the current disk space usage for all mounted filesystems?

Answer: `df`

12. Weird text

13.  When considering the use of hard links, what are valid reasons to not use hard links?

Answer: Hard links are specified to one filesystem and cannot point to files on another filesystem.

14. In compliance with the FHS, in which of the directories are man pages found?

Answer: `/usr/share/man/`

15. Which file in the `/proc` filesystem lists parameters passed from the bootloader to the kernel?

Answer: `cmdline`

16. What is the process ID number of the init process on a System V init based system?

Answer: 1

17. Which daemon handles power management events on Linux systems?

Answer: `acpid`

18. Which of the following statements are true about the boot sequence of a PC using a BIOS?

Answers:
1. Some parts of the boot process can be configured from the BIOS.
2. The BIOS initiates the boot process after turning the commputer on.

19. What is true regarding UEFI firmware?

Answers:
1. It can use and read certain file systems.
2. It is stored in a special area within the GPT metadata

20. Weird text

21. When is the content of the kernel ring buffer reset?

Answers:
1. When the ring buffer is explicitly reset using the command `dmseg -clear`
2. When the system is shut down or rebooted

22. What is the first program the Linux kernel starts at boot time when using System V init?

Answer: `/sbin/init`

23. Weird text

24. What is contained on the EFI System Partition?

Answer: The first stage boot loader

25. Which of the following directories on a 64-bit Linux system typically contain shared libraries?

Answers:
1. `/usr/lib64`
2. `/lib64`

---

Resources:
https://www.itexams.com/exam/101-500