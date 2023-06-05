#linux 

The `/etc` directory is contained in the root directory (`/`).

The `/etc` directory mainly contains **system configuration information**. Configuration files affect the behavior of the storage system. You can use an editor on your administration host to edit some configuration files in this directory.
 
The `/etc` directory maintains a lot of files. Some of them are described below. For others, you should determine which program they belong to and read the manual page for that program.

Many networking configuration files are in `/etc` as well, and are described in the `Networking Administrations' Guide`.

`/etc/rc` or `/etc/rc.d` or `/etc/rc?.d` - scrips or directories that run at startup or when changing the run level.

`/etc/passwd` - the user database, with fields giving the username, real name, home directory, and other information about each user.

`/etc/shadow` - an encrypted file that holds user passwords

`/etc/fdprm` - floppy disk parameter table. Describes what different floppy disk formats look like. It's used by `setfdprm`.

`/etc/fstab` - lists the filesystems mounted automatically at startup by the `mount -a` command. Under Linux, also contains information about swap areas used automatically by `swapon -a`.

`/etc/group` - similar to `/etc/passwd`, but describes groups instead of users.

`/etc/inittab` - configuration file for `init`

`/etc/issue` - output by `getty` before the login prompt. Contains the descriptions of various files formats based on which file guesses the type of the fule.

