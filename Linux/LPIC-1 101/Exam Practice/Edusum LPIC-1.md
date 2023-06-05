#linux #LPIC-1 

1. You have a set of libraries that were installed into `/usr/local/lib` and would like to ensure that the libraries are also available in `/usr/lib`. What is the preffered way to make the libraries available in this location?

Answer: Create a `symbolic link`.

2. The program is a handy tool for repairing corrupted filesystems.

Answer: `fsck`.

3. Which option to `lsblk` shows the UUID of each filesystem?

Answer: `-f`. Example:

```shell
$ lsblk -f
```

4. Steve is working on an open source software development team to create a new application. He's completed a new shared library the program will be using and has moved it to the correct location. What command should Steve employ to update the system's library cache?

Answer: `ldconfig`.

5. Carol used the `ps` command to find the process ID of an application that she needs to stop. What command-line tool should she use to stop the application?

Answer: `kill`.

6. What command must you run to install GRUB Legacy to the MBR?

Answer: `grub-install`.

7. Kilo has just cloned 10 VMs from a clone system image. He needs to ensure that the clones can all run together on the same local network segment. What items should he check and modify if needed?

Answer: `NIC MAC address`, `Host name`, `Machine ID`.

8. A user who is a member of the custom admins group is attempting to read the contents of a file but is not the owner of the file. Rather than granting sudo access to this file, what is another way to grand read access, assuming the file is currently marked with `640 permissions`?

Answer: Use `chgrp` to change the group ownership to admins.

9. Which utility is used for formatting GTP disks?

Answer: `gdisk`.

10. Which signal number is used as `SIGKILL` when used with the kill command?

Answer: 9.