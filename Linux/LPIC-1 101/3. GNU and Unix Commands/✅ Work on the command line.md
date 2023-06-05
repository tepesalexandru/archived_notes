#linux #LPIC-1 

## Getting System Information
The most important command you have access to in the Linux terminal is `pwd`. This command tells you in which directory you're currently situated. The `pwd` command is short for "print working directory."

```shell
$ pwd 

# Example: outputs /home/frank
```

The next most important command is `ls`, which displays the contents of the directory you're corrently in.

Another important command is `touch <filename>` which gives you the ability to create new files.

```shell
$ touch hello.txt
$ ls

# Outputs hello.txt
```

Besides your location in the filesystem, you will often want information about the Linux system you are running. The `uname` tool is what you are after here. In particulare, `uname -a` ("a" stands for "all").

```shell
$ uname -a

# Example: outputs Linux ubuntu 5.4.0-88-generic #99-Ubuntu SMP Thu Sep 23 17:29:00 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

## Getting Command Information
You will often come across documentation talking about Linux commands with which you are not yet familiar yet. The command line itself offers all kinds of helpful information on what commands do and how to effectively use them. Perhaps the most useful information is found within the many files of the `man` system.

Typing `man` followed by the name of a command will give you information that includes the command name, a brief usage synpopsis, a more detailed description, and some important historical and licensing background. As an example:

```shell
$ man uname

UNAME(1)             User Commands            UNAME(1)
NAME
   uname - print system information
SYNOPSIS
   uname [OPTION]...
DESCRIPTION
   Print certain system information.  With no OPTION, same as -s.
   -a, --all
      print  all information, in the following order, except omit -p
      and -i if unknown:
   -s, --kernel-name
      print the kernel name
   -n, --nodename
      print the network node hostname
   -r, --kernel-release
      print the kernel release
   -v, --kernel-version
      print the kernel version
   -m, --machine
      print the machine hardware name
   -p, --processor
      print the processor type (non-portable)
   -i, --hardware-platform
      print the hardware platform (non-portable)
   -o, --operating-system
      print the operating system
   --help display this help and exit
   --version
      output version information and exit
AUTHOR
   Written by David MacKenzie.
REPORTING BUGS
   GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
   Report uname translation bugs to
   <http://translationproject.org/team/>
COPYRIGHT
   Copyright©2017 Free Software Foundation, Inc. License  GPLv3+: GNU
   GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
   This is free software: you are free to change and redistribute it.
   There is NO WARRANTY, to the extent permitted by law.
SEE ALSO
   arch(1), uname(2)
   Full documentation at: <http://www.gnu.org/software/coreutils/uname>
   or available locally via: info '(coreutils) uname invocation'
GNU coreutils 8.28       January 2018             UNAME(1)

```

### apropos

`man` only works when you give it an exact command name. If, however, you are not sure about the name of the command you are after, you can use the `apropos` command to search through the `man` page names and descriptions. Assuming, for instance, that you cannot remember that it is `uname` that will give you your current Linux kernel version, you can pass the word "kernel" to `apropos`. You will probably get many lines of output, but they should include these:

```shell
$ apropos kernel

systemd-udevd-kernel.socket (8) - Device event managing daemon
uname (2)            - get name and information about current kernel
urandom (4)          - kernel random number source devices

```

### type

If you do not need a command's full documentation, you can quickly get basic data about a command using `type`.  As an example:

```shell
$ type uname cp kill which

uname is hashed (/bin/uname)
cp is /bin/cp
kill is a shell builtin
which is /usr/bin/which
```

### which
Sometimes - particularly when working with automated scripts - you will need a simpler source of information about a command. The `which` command that our previous `type` command traced for us, will return nothing but the `absolute location` of a command. As an example:

```shell
$ which uname which

/bin/uname
/usr/bin/which
```

## Using Your Command History
Typing `history` will return the most recent commands you have executed with the most recent of those appearing last. You can easily search through those commands by piping a specific string to the `grep` command. This example will search for any command that includes the text `bash_hostory`:

```shell
$ history | grep bash_history

1605 sudo find /home -name ".bash_history" | xargs grep sudo
```

What is in the `.bash_history` file? It contains hundreds and hundreds of your most recent commands. However, your most recent commands are missing from the file, as they are first dynamically added to the `history` database, and will be written to the `.bash_history` file only when you exit your session.

## Finding Your Environment Variables
You can output every environment variable currently present in your Linux system using the `env` command:

```shell
$ env

# Example output: 
# SHELL=/bin/bash
# PWD=/root
# LOGNAME=kc-internal
# HOME=/root
```

## Creating New Environment Variables
You can add your own custom variables to your environment. The simplest way is to use the `=` character. The string to the left will be the name of your new variable, and the string to the right will be its value.

You can also display the value of a variable using the `echo` command.

```shell
$ x=Alex
$ echo $x

# Output: Alex
```

You can use the `bash` command in order to open up a new shell, which will not contain the previous environment variables. The new created shell will be a *child* of the original shell (the *parent*).

A variable you create is only going to be availably locally, within the immediate shell session. If you start up a new shell, or close down the session using `exit`, the variable will not go along with you.

The `exit` command will close the current shell session and bring you back to the parent shell.

The `export` command allows you to pass an environment variable to child shells. Therefore, the following example works:

```shell
$ myvar=Hello
$ export myvar
$ bash
$ echo $myvar

Hello
```

## Deleting Environment Variables
One way of deleting all environment variables that you've created is by deleting their parent shell or by rebooting the computer. Of course, there is a simpler way. The `unset` command will kill any variable passes as parameter:

```shell
$ unset x
$ echo $x

# Outputs: nothing
```

If there is an `unset` command, then you can bet there must be a `set` command to go with it. Running `set` by itself is very similar in output as for the `env` command. However, the difference between `set` and `env` is that `set` will output all variables *and functions*.

## Quoting to Escape Special Characters
If you try to create a file named `my big file` using the touch command, it will result in the following:

```shell
$ touch my big file
$ ls

my big file
```

Three separate files have been created, since the space character ` ` was used. In order to escape special characters, you will need to enclose the name in `quotation marks` :

```shell
$ touch "my big file"
$ ls

'my big file'
```

In this example, only one file has been created.

---

Concepts in this lesson:
-   ✅ `bash`
-   ✅ `echo`
-   ✅ `env`
-   ✅ `export`
-   ✅ `pwd`
-   ✅ `set`
-   ✅ `unset`
-   ✅ `type`
-   ✅ `which`
-   ✅ `man`
-   ✅ `uname`
-   ✅ `history`
-   ✅ `.bash_history`
-   ✅ Quoting
