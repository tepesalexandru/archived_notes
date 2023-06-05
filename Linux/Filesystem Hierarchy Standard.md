#linux 

The Filesystem Hierarchy Standard (**FHS**) is a reference describing the conventions used for the layout of a UNIX system.

### Directory Structure
`/` - **primary hierarchy root** and **root directory** of the entire file system hierarchy
`/bin` - essential command **bin**aries that need to be available in single-user mode, including to bring up the system or repair it, for all users.
`/boot` - **boot** loader files
`/dev` - **dev**ice files
`/etc` - host-specific system-wide configuration files. See more on [[The etc directory]]
`/etc/opt` - configuration files for add-on packages sotred in `/opt`
`/etc/sgml` - configuration files, such as catalogs, for software that processes SGML
`/etc/X11` - configuration files for the X Window System, version 11
`/etc/xml` - configuration files, such as catalogs, for software that processes XML
`/home` - the user's **home** directories, containing saved files, personal settings, etc.
`/root` - the home directory for the **root** user.
`/sbin` - essential **s**ystem **bin**aries
`/lib` - **lib**raries essential for the binaries in `/bin` and `/sbin`
`/media` - mount points for removable **media** such as CD-ROMs
`/sys` - contains information about devices, drivers, and some kernel features
`/var` - **var**iable files, files whose content is excpected to continually change during normal operaion of the system, such as logs, spool files, and temporary e-mail files.
`/usr` - secondary hierarchy for read-only **us**e**r** data; contains the majority of (multi-)user utilities and applications. Should be shareable and read-only.
`/tmp` - directory for **t**e**mp**orary files. Often not preserved btween system reboots and may be severely size-restricted.