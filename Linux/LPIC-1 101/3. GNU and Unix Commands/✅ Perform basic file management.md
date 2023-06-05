#linux #LPIC-1 

# Part 1
## Introduction
Everything in Linux is a file, so knowing how to manipulate them is very important. In this lesson, we shall cover basic operations on files.

A `file` is an entity that stores data and programs. It consists of content and meta data (e.g. file size, owner, creation date, permissions). Files are organized in `directories`. A directory is a file that stores other files.

The three main types of files on a Linux system are:
- Regular files - store data and programs
- Directories - contain other files
- Special files - are used for input and output

Other types of files exist, but they are byond the scope of this lesson.

## Using `ls` to List Files
The `ls` command is one of the most important command line tools you should learn in order to navigate the file system. In its basic form, `ls` will list file and directories names *only*:

```shell
$ ls

Desktop Downloads emp_salary file1 Music Public Videos # etc.
```

When used with `-l`, referred to as "long list" format, it shows file or directory permissions, owner, size, modified date, time and name:

```shell
$ ls

total 60
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Desktop
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Documents
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Downloads
-rw-r--r--  1   frank   frank     21    Sep 7   12:59   emp_name
-rw-r--r--  1   frank   frank     20    Sep 7   13:03   emp_salary
-rw-r--r--  1   frank   frank   8980    Apr 1   2018    examples.desktop
-rw-r--r--  1   frank   frank     10    Sep 1   2018    file1
-rw-r--r--  1   frank   frank     10    Sep 1   2018    file2
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Music
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Pictures
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Public
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Templates
drwxr-xr-x  2   frank   frank   4096    Apr 1   2018    Videos

```

The first character in the output indicates the file type:
- `-` - regular file
- `d` - directory
- `c` - special file

To show the file sizes in a human readable format, use the parameter `-lh` instead.

In order to display all files, including the hidden ones (those starting with `.`), use the option `-a`:

```shell
$ ls -a

.               .dbus   file1   .profile
..              Desktop file2   Public
.bash_history   .dmrc  .gconf  .sudo_as_admin_successful
```

## Creating, Copying, Moving and Deleting Files
### Create files with `touch`
The `touch` command is the easiest way to create new, empty files. You can also use it to change the timestamps (i.e. modification time) of existing files and directories. For example:

```shell
$ touch file1 file2 file3 # Will create three new files named "file1", "file2" and "file3"
```

### Copying files with `cp`
As a Linux user, you will often copy files from one location to another. The `cp` command is perfect for copying files. As an example usage:

```shell
$ cp file1 dir2 # Copies file named "file1" into the directory "dir2"
```

### Moving files with `mv`
Just like the `cp` command for copying, Linux provides a command for moving and renaming files, called `mv`.

The move operation is analogue to the cut and paste operation you generally perform through a Graphical User Interface (GUI). If you wish to move a file into a new location, use `mv` in the following way:

```shell
$ mv file1 dir2 # Moves the file named "file1" into the directory "dir2"
```

You can also rename a file using the `mv` command in the following way:

```shell
$ mv old_name new_name # Renames the file
```

You can also provide the `-i` option in order to ask for user confirmation:

```shell
$ mv -i old_name new_name

mv: overwrite "old_name"?
```

### Deleting files with `rm`
`rm` is used to delete files. Think of it as an abbreviation form of the word "remove". The action of removing a file is usually irreversible thus this command should be used with caution. An example:

```shell
$ rm file1 # Deletes the file named "file1"
$ rm -i file1 # Deletes the file named "file1", but asks for permission first
$ rm file1 file2 file3 # Deletes files named "file1", "file2", and "file3"
```

## Creating and Deleting Directories
### Create directories with `mkdir`
Creating directories is critical to organizing your files and folders. Files may be grouped together in a logical way by keeping them inside a directory. To create a directory, use `mkdir`:

```shell
$ mkdir dir1 # Creates a directory named "dir1"
$ mkdir dir1 dir2 dir3 # Creates three directories, "dir1", "dir2", and "dir3"
```

### Removing directories with `rmdir`
`rmdir` removes a directory *if it is empty*. An example would be:

```shell
$ rmdir dir1 # Deletes the directory "dir1"
$ rmdir dir1 dir2 # Deletes the directories "dir1" and "dir2"
```

### File Globbing and Wildcards
File `globbing` is a feature provided by the Unix/Linux shell to represent multiple filenames by using special characters called `wildcards`.

Wildcards are essentially symbols which may be used to substitute for one or more characters. They allow, for example, to show all files that start with the latter A or all files that end with the letters `.conf`.

Below are some examples of file globbing:

```bash
# Delete all files in the current working directory
rm *

# List all files with names beginning with l followed by any single character and ending with st 
ls l?st

# Remove all directories whose name starts with a letter
rmdir [a-z]*
```

# Part 2
## How to find files
As you use your machine, files progressively grow in number and size. Sometimes it becomes difficult to locate a particular file.

Linux provides `find` to quickly search and locate files. It has the following syntax:

```shell
$ find STARTING_PATH OPTIONS EXPRESSION
```

- `STARTING_PATH` - defines the directory where the search begins
- `OPTIONS` - controls the behaviour and adds specific criteria to optimize the search process
- `EXPRESSION` - defines the search query

As an example:

```shell
$ find . -name "myfile.txt"
```

The starting path in this case is the current directory (denoted by the `.`).
The option `-name` specifies that the search result is based on the name of the file ("myfile.txt")

### Using Criteria to Speed Search
You can use the `find` command to locate files based on their `type`, `size`, or `time`. When searching based on these criteria, the amount of files searched is reduced and the results are obtained in less time.

For example, in order to search by a specific type:
- `-type f` - file search
- `-type d` - directory search
- `-type l` - symbolic link search

As an example:

```shell
$ find . -type d -name "Games"
```

This command finds all directories in the current directory and below, that have the name `example`.

## Archiving Files
The `tar` command, short for "tape archive(r)", is used to create tar archives by converting a group of files into an archive.

Archives are created so as to easily move or backup a group of files. Think of `tar` as a tool that creates a glue onto which files can be attached, grouped, and easily moved.

`tar` also has the ability to extract tar archives, display a list of the files included in the archive as well as add additional files to an existing archive. It has the following syntax:

```shell
$ tar [OPERATION_AND_OPTIONS] [ARCHIVE_NAME] [FILE_NAME(S)]
```

- OPERATION - only one operation is allowed, it can either be:
	- `--create` - create a new tar archive
	- `--extract` - extract the entire archive or one or more files from an archive
	- `--list` - display a list of the files included in the archive

- OPTIONS - frequently used are:
	- `--verbose` - shows the files being processed by the `tar` command
	- `--file=archive-name` - specifies the archive file name
- ARCHIVE_NAME - the name of the archive
- FILE_NAME(S) - a space-separated list of file names to be extracted. If not provided, the entire archive is extracted.

### Creating an archive

An example of archiving an archive from a directory inside our current directory is the following:

```bash
$ tar -cvf archive.tar stuff
```

The command above archives the `stuff` directory into the `archive.tar` file. The parameters mean:
`-c`: create an archive
`-v`: display progress while creating the archive
`-f`: specify the name of the archive

You can also archive multiple directories and files into a single archive, with the following syntax:

```shell
$ tar -cvf archive.tar DIRECTORY1 DIRECTORY2 ... FILE1
```

### Extracting an archive
In order to extract an archive, the following command is used:

```shell
$ tar -xvf archive.tar
```

Where `archive.tar` in this case is the archive we want to extract

If we want to extract it to a specific directory, we can add the `-C` parameter:

```shell
$ tar -xvf archive.tar -C /tmp
```

The command above will extract the files into the `/tmp` directory.

You can also use two different compressing methods: `bzip2` and `gzip`. 
The `-j` parameter is used for `bzip2`, having the `.tar.bz` extension. 
The `-z` parameter is used for `gzip`, having the `.tar.gz` extension.

In order to decompress these files, simply use `-x` (coming from "eXtract") instead of `-c` (coming from "Create").

## The `cpio` command
The `cpio` command stands for Copy In, Copy Out. It is used to process archive files such as `*.cpio` or `*.tar` files.This command is used for:
- copying files to an archive
- extracting files from an archive

Here are the two most common `cpio` commands:

```bash
# To create a cpio archive
ls | cpio -o -> archive.cpio

# To extract the archive
cpio -id < archive.cpio
```

## The `dd` command
THe `dd` command copies data from one location to another. It has the following syntax:

```shell
$ dd if=oldfile of=newfile
```

Where `if` stands for `input file` and `of` for `output file`.

---

#### Concepts in this lesson:
-   ✅ `cp`
-   ✅ `find`
-   ✅ `mkdir`
-   ✅ `mv`
-   ✅ `ls`
-   ✅ `rm`
-   ✅ `rmdir`
-   ✅ `touch`
-   ✅ `tar`
-   ✅ `cpio`
-   ✅ `dd`
-   ✅`file`
-   ✅ `gzip`
-   ✅ `gunzip`
-   ✅ `bzip2`
-   ✅ `bunzip2`
-   ✅ file globbing
