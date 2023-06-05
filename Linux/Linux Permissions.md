#linux 

There are three kinds of file permissions in Linux:
1. **Read** (r) - Allows a user or group to view a file.
2. **Write** (w) - Permits the user to write or modify a file or directory.
3. **Execute** (x) - A user or group can execute a file or view a directory.

In order to change the permission of a file in Linux, use the `chmod` command.

There are three kinds of permission groups in Linux:
1. **Owners** - by default, the person who created the file.
2. **Groups** - contains multiple users
3. **All users** - contains all users in the system

File permission can be seen with the command `ls -l`.

For example, the string `-rw-rw-r--` can be broken down in three parts:
1. `rw-` indicates that the owner can read and write to the file, but not execute
2. `rw-` same as the owner, but for the entire group
3. `r--` all other users can only read the file, but not write to it

The three commands used in order to work with permissions in Linux are:
1. `chmod` - used to change file permissions
2. `chown` - used to change the owner of a file
3. `chgrp` - used to change the user group of the owner of a file

The syntax for chmod is the following:

```bash
chmod [ugoa] [+-=] [rwx] path(s)
```

The syntax for chown is the following:

```bash
chown [options] new_owner_name path(s)
```

The syntax for chgrp is the following:

```bash
chgrp [options] new_group_name path(s)
```

For the chown and chgrp, it's common to use the `-R` option in order to recuresively change the permissions in all the files present in a directory.