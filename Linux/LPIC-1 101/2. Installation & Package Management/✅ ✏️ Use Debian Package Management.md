#linux #LPIC-1 

## Introduction
A long time ago, when Linux was still in its infancy, the most common way to distribute software was a compressed file (usually a `.tar.gz` archive) with source code, which you would unpack and compile yourself.

However, as the amount and complexity of software grew, the need for a way to distribute pre-compiled software became clear. After all, not everyone had the resources, both in time and computing power, to compile large projects like the Linux kernel or an X Server.

Soon, efforts to standardzie a way to distribute these software "packages" grew, and the first `package managers` were born. These tools made it much easier to install, configure or remove software from a system.

One of those was the Debian package format (`.deb`) and its package tool (`dpkg`). Today, they are widely used not only on Debian itself, but also on its derivates, like Ubuntu and those derived from it.

Another package management tool that is popular on Debian-based systems is the `Advanced Package Tool` (`apt`), which can streamline many of the aspects of the installation, maintenance and removal of packages, making it much easier.

## The Debian Package Tool (dpkg)
The *Debian Package* (`dpkg`) tool is the essential utility to install, configure, maintain and remove software packages on Debian-based systems. The most basic operation is to install a `.deb` package, which can be done with:

```shell
$ dpkg -i PACKAGE_NAME
```

Let's take a look over a list of possible commands when using dpkg:

```shell
$ dpkg -i # Installs a single package, or a space-separated list of packages

$ dpkg -r # Removes a package, or a space-separated list of packages

$ dpkg -I # Inspects a package, providing details on the software it installs and any needed dependencies

$ dpkg --get-selections # Lists out every package that dpkg has installed on the system
$ dpkg -L # Prints out a list of every file that a particular package installs

$ dpkg-query # WIth a specified file name, this command will print out the package that installed the file

$ dpkg-reconfigure # This command will re-run a packages post-install script so that an administrator can make configuration adjustments to the package's installation
```

Also, a list for apt commands:

```shell
$ apt-get update # Updates the local package index to match what is available within the configured repositories under the /etc/apt directory

$ apt-get install # Downloads a package from a remote repository and install it along with its dependencies, can also be used to install a Debian package that has already been downloaded

$ apt-get remove # Uninstalls the specified package(s) from the system

$ apt-cache show # Just like the dpkg -I command, this command can be used to show details on a specified package

$ apt-cache search # Search your local APT cached database for a particular package

$ apt-file update # Update the package cache so that the apt-file command can query its contents

$ apt-file search # Search in which package a file is included. A list of all packages containing the pattern is returned.

$ apt-file list # List all the contents of a package, just like the dpkg -L command
```

### The Sources List
APT uses a list of sources to know where to get packages from. This list is stored in the file `sources.list` located inside the `/etc/apt` directory.

This file can be edited directly with a text editor, like `vi`, or with graphical utilities like `aptitude` or `synaptic`.

A typical line inside `sources.list` looks like this:

```bash
deb http://us.archive.ubuntu.com/ubuntu/ disco main restricted universe multiverse
```

---
Concepts in this lesson:
-   ✅ `/etc/apt/sources.list` 
-   ✅ `dpkg` 
-   ✅ `dpkg-reconfigure` 
-   ✅ `apt-get` 
-   ✅ `apt-cache` 

---

###  ✏️ Guided Exercises
1. What is the command to install a package named `package.deb` using `dpkg`?

✅ `dpkg -i package.deb`

2. Using `dpkg-query`, find which package contains a file named `7zr.1.gr`.

✅ `dpkg-query -S 7zr.1.gr`

3. Can you remove a package called `unzip` from the system using `dpkg -r unzip` if the package `file-roller` depends on it? If not, what would be the correct way to do it?

The `unzip` package can't be removed because `file-roller` depends on it. First, remove `file-roller`, and then the `unzip` package.

✅ `dpkg -r unzip file-roller`.

4. Using `apt-file`, how can you find out which package contains the file `unrar`?

✅ `apt-file search unrar`.

5. Using `apt-cache`, what is the command to show information for the package `gimp`?

✅ `apt-cache show gimp`