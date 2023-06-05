#linux #LPIC-1 


One thing that most Linux distributions have in common is the `Filesystem Hierarchy Standard` (FHS), which defines a *standard layout* for the filesystem.

### The `find` command
To search for files on a Linux system, you can use the `find` command. To start, `find` needs two arguments: a *starting point* and *what to look for*.

For instance, to search for all files in the current directory (and subdirectories) whose name ends with `.jpg`:

```bash
find . -name '*.jpg'
./pixel_3a_seethrough_1.jpg
./Mate3.jpg
./Expert.jpg
./Pentaro.jpg
./Mate1.jpg
./Mate2.jpg
./Sala.jpg
./Hotbit.jpg
```
### `locate` and `updatedb`
`locate` and `updatedb` are commands that can be used to quickly find a file matching a given pattern on a Linux system.

Unlike `find`, it will not search the filesystem for the pattern, but a database instead. The database from which it finds files is updated by `updatedb`.

This is faster than `find`, because there are less files, but it may have out of date information depending on when was the last `updatedb` executed.

```bash
locate jpg
/home/carol/Downloads/Expert.jpg
/home/carol/Downloads/Hotbit.jpg
/home/carol/Downloads/Mate1.jpg
/home/carol/Downloads/Mate2.jpg
/home/carol/Downloads/Mate3.jpg
/home/carol/Downloads/Pentaro.jpg
/home/carol/Downloads/Sala.jpg
/home/carol/Downloads/pixel_3a_seethrough_1.jpg
/home/carol/Downloads/jpg_specs.doc
```
You can control the behavior of `updatedb` in the file `/etc/updatedb.conf`.

### Finding binaries, manual pages, and source code
`which` is a useful command that shows the full path to an executable.

```bash
which bash
/usr/bin/bash
```
`type` is a similar command which will show information about a binary, including where it is located and its type.

```bash
type bash
bash is /usr/bin/bash

type -t ll # THe -t flag shows the type of the file
alias
```
The type of a file (using `type`) can either be *alias*, *keyword*, *function*, *builtin*, or *file*.

The command `whereis` is more versatile binaries can also be used to show the location of man pages or even source code for a program.

```bash
whereis bash
# Last one is the compressed manual pages
bash: /usr/bin/bash /usr/share/man/man1/bash.1.gz 
```

---

Key knowledge areas
• Understand the correct locations of files under the FHS.
• Find files and commands on a Linux system.
• Know the location and purpose of important file and directories as defined in the FHS.
Partial list of the used files, terms and utilities
- ✅ `find`
- ✅ `locate`
- ✅ `updatedb`
- ✅ `whereis`
- ✅ `which`
- ✅ `type`
- ✅ `/etc/updatedb.conf`