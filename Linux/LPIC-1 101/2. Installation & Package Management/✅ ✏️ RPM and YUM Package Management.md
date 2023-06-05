#linux #LPIC-1 

## Introduction
A long time ago, when Linux was still in its infancy, the most common way to distribute software was a compressed file (usually a `.tar.gz` archive) with source code, which you would unpack and compile yourself.

Soon, efforts to standardize a way to distribute these software "packages" grew, and the first package managers were born. These tools made it much easier to install, configure or remove software from a system.

One of those was the *RPM Package Manager* and its corresponding tool (`rpm`), developed by Red Hat.

## The RPM Package Manager (`rpm`)
### Installing, Upgrading and Removing Packages
The most basic operation is to install a package, which can be done with:

```shell
$ rpm -i PACKAGE_NAME # Installs a package
$ rpm -ih PACKAGE_NAME # Installs a package with progress bar
```

Where PACKAGE_NAME is the name of the `.rpm` package you wish to install.

If there is a previous version of a package on the system, you can upgrade to a newer version using the `-U` parameter:

```shell
$ rpm -U PACKAGE_NAME # Updates a package
```

If there is no previous version of PACKAGE_NAME installed, then a fresh copy will be installed.


To remove an installed package, pass the `-e` parameter (as in "erase") to `rpm`, followed by the name of the package you wish to remove:

```shell
$ rpm -e PACKAGE_NAME # Erases a package
```

To find out which installed package owns a file, use the `-qf` ("query file") followed by the full path to the file:

```bash
rpm -qf /usr/bin/unzip
unzip-6.0-19.el7.x86_64
```


## YellowDog Updater Modified (`yum`)
`yum` was originally developed as the *Yellow Dog Updater* (YUP), a tool for package management on the Yellow Dog Linux distribution.

Functionally, it is similar to the `apt` utility on Debian-based systems, being able to search for, install, update, and remove package and automatically handle dependencies. `yum` can be used to install a single package, or to upgrade a whole system at once.

The following are the basic commands when using `yum`:

```shell
$ yum install PACKAGE_NAME
$ yum update PACKAGE_NAME
$ yum remove PACKAGE_NAME
```

By running `yum check-update`, you can also update all packages in the system.

### Managing Software Repositories
For `yum`, the "repos" are listed in the directory `/etc/yum.repos.d/`. Each repository is represented by a `.repo` file, like `CentOS-Base.repo`.

Additionally, extra repositories can be added by the user by adding a `.repo` file in the directory mentioned above, or at the end of `/etc/yum.conf`. However, the recommended way to add or manage repositories is with the `yum-config-manager` tool.

To add a repository, use the `--add-repo` parameter, followed by the URL to a `.repo` file. Example usage:

```shell
$ yum-config-manager --add-repo REPO_URL
```

To get a list of all available repositories, use the `yum repolist all` command. You will get an output similar to this:

```shell
$ yum repolist all

Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * base: mirror.ufscar.br
 * epel: mirror.globo.com
 * extras: mirror.ufscar.br
 * updates: mirror.ufscar.br
repo id                       repo name                    status
updates/7/x86_64              CentOS-7 - Updates           enabled:  2,500
updates-source/7              CentOS-7 - Updates Sources   disabled
```

## DNF
`dnf` is the package management tool used on Fedora, and is a fork of `yum`. As such, many of the commands and parameters are similar.

### Managing Software Repositories
Just as with `yum` and `zypper`, `dnf` works with software repositories (repos). Each distributions has a list of default repositories, and administrators can add or remove repos as needed.

To get a list of all available repositories, use `dnf repolist`. As an example:

```shell
$ dnf repolist

Last metadata expiration check: 0:20:09 ago on Sat 21 Sep 2019 02:39:43 PM -03.
repo id                    repo name                                      status
*fedora                    Fedora 30 - x86_64                             56,582
*fedora-modular            Fedora Modular 30 - x86_64                        135
*updates                   Fedora 30 - x86_64 - Updates                   12,774
*updates-modular           Fedora Modular 30 - x86_64 - Updates              145
```

## Zypper
`zypper` is the package management tool used on SUSE Linux and OpenSUSE. Feature-wise it is similar to `apt` and `yum`, being able to install, update, and remove packages from a system, with automated dependency resolution.

### Updating the Package Index
Like other package management tools, `zypper` works with repositories containing packages and metadata. This metadata needs to be refreshed from time to time, so that the utility will know about the latest packages available. In order to refresh, use the following command:

```shell
$ zypper refresh

Repository 'Non-OSS Repository' is up to date.
Repository 'Main Repository' is up to date.
Repository 'Main Update Repository' is up to date.
Repository 'Update Repository (Non-Oss)' is up to date.
All repositories have been refreshed.
```

#### Managing Software Repositories
`zypper` can also be used to manage software repositories.

```bash
zypper repos # SHows all repositories currently registred in the system
zypper modifyrepo -d REPO_NAME # Disabled REPO_NAME
```

---

Concepts in this lesson:
-   ✅ `rpm`
-   ✅ `rpm2cpio`
-   ✅ `/etc/yum.conf`
-   ✅ `/etc/yum.repos.d/`
-   ✅ `yum`
-   ✅ `zypper`

---

###  ✏️ Guided Exercises
1. Using `rpm` on a Red Hat Enterprise Linux system, how would you install the package `file-roller-3.28.1-2.el7_x86_64.rpm` showing a progress bar during the installation?

✅ `rpm -ih file-roller-3.28.1-2.el7_x86_64.rpm`.

2. Using `rpm`, find out which package contains the file `/etc/redhat-release`

✅ `rpm -qf /etc/redhat-release`

3. How would you use `yum` to check for updates for all packages in the system?

✅ `yum check-update`.

4. Using `zypper`, how would you disable a repository called `repo-extras`?

✅ `zypper modifyrepo -d repo-extras`.

5. If you have a `.repo` file describing a new repository, where this file should be put so that it is recognized by DNF?

✅ `/etc/yum.repos.d/`