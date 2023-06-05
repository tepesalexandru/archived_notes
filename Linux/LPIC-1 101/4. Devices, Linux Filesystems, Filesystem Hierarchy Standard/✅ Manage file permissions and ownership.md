#linux #LPIC-1 

Being a multi-user system, Linux needs to track who owns each file and wheher or not a user is allowed to perform actions on a file. This is done by a three-level permissions system.

Every file is owner by a *user* and a *user group*, and has three sets of permissions:
1. one for the owner
2. one for the group who owns the ifle
3. one for everyone else (sometime referred to as *world*)

### Querying Information about FIles and Directories
By using `ls -l` (long form), you can see the permission of each file:

```bash
ls -l
total 536
drwxrwxr-x 2 carol carol 4096 Dec 10 15:57 Another_Directory
-rw------- 1 carol carol 539663 Dec 10 10:43 picture.jpg
-rw-rw-r-- 1 carol carol 1881 Dec 10 15:57 text.txt
```
The first column from the previous command shows the file type and permissions.

You can also query hidden files with the following command:

```bash
ls -l -a # The -a flag shoes hidden files
# Or, shorthand
ls -la
total 544
drwxrwxr-x 3 carol carol4096 Dec 10 16:01 .
drwxrwxr-x 4 carol carol4096 Dec 10 15:56 ..
drwxrwxr-x 2 carol carol4096 Dec 10 17:59 Another_Directory
-rw------- 1 carol carol 539663 Dec 10 10:43 picture.jpg
-rw-rw-r-- 1 carol carol 1881 Dec 10 15:57 text.txt
-rw-r--r-- 1 carol carol 0 Dec 10 16:01 .thisIsHidden
```
Hidden files are simply files that start with a `dot` " . ";

### Permissions on Files
`r` stands for *read* and has an octal value of 4. You can open a file and read its contents.
`w` stands for *write* and has an octal value of 2. You can edit or delete a file.
`x` stands for *execute* and has an octal value of 1. You can run the file as an executable.

### Permissions on Directories
`r` stands for *read* and has an octal value of 4. You can read the directory's contents (filenames).
`w` stands for *write* and has an octal value of 2. You can create or delete files in a directory.
`x` stands for *execute* and has an octal value of 1. You can enter a directory.

### Modifying File Permissions
The command `chmod` is used to modify the permissions of a file. Only the owner of a file or the root user can change the permissions of a file.

### Modifying File Ownership
The command `chown` is used to modify the ownership of a file or directory.

```bash
chown USERNAME:GROUPNAME FILENAME
```
### Querying Groups
You can list all user groups in the system by using the following command:

```bash
getent group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,rigues
tty:x:5:rigues
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:rigues
```
Or, narrow it down to a specific user:

```bash
groups alex
alex : alex adm cdrom sudo dip plugdev lpadmin lxd sambashare
```
### Default Permissions
When creating a new file or directory, the default permissions on that file come from the *user mask*. You can view the user mask with the `umask` command:
```bash
umask
0002
```
Or, in a more readable form:
```bash
umask -S
u=rwx,g=rwx,o=rx
```
You can also change your user mask for the current shell session:

```bash
umask u=rwx,g=rwx,o=
```


---

Key knowledge areas
• Manage access permissions on regular and special files as well as directories.
• Use access modes such as suid, sgid and the sticky bit to maintain security.
• Know how to change the file creation mask.
• Use the group field to grant file access to group members.
Partial list of the used files, terms and utilities
- ✅ `chmod`
- ✅ `umask`
- ✅ `chown`
- ✅ `chgrp`