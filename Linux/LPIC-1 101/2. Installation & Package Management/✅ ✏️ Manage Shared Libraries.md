#linux #LPIC-1 

## Introduction
In this lesson we will be discussing `shared libraries`, also known as `shared objects`: pieces of compiled, reusable code like functions or classes, that are recurrently used by various programs.

## Concept of Shared Libraries
To build an `executable file` from the program's `source code`, two important steps are necessary. 

First, the `compiler` turns the source code into machine code that is stored in so-called `object files`. Secondly, the `linker` combines the object files and *links* them to libraries in order to generate the final executable file. This linking can be done `statically` or `dynamically`.

Depending on which method we go for, we will be talking about `static libraries` or, in case of dynamic linking, about `shared libraries`.

### Static Libraries
A static library is merged with the program at link time. A copy of the library code is embedded into the program and becomes part of it. Thus, the program ahs no dependencies on the library at run time becasue the program already contains the libraries code. Having no dependencies can be seen as an advantage since you do not have to worry about making sure the used libraries are always available. On the downside, statically linked porgrams are heavier.

### Shared (or Dynamic) Libraries
In the case of shared libraries, the linker simply takes care that the program references libraries correctly. The linker does, however, not copy any librari code into the program file. At run time, though, the shared library must be available to satify the program's dependencies. This is an economical approach to managing system resources as it helps reduce the size of program files and only one copy of the library is loaded in memory, even when it is used by multiple programs.

## Shared Object File Naming Conventions
The name of a shared library, also known as `soname`, follows a pattern which is made up of three elements:
- Library Name - usually prefixed by `lib`
- `so` - stands for "shared object"
- Version Number of the library

An example would be `libpthread.so.0`.

By contrast, static library names usually end in `.a`, e.g. `libthread.a`.

Common locations for shared libraries in a Linux system are: `/lib`, `/lib32`, `/lib64`, `/usr/lib`, `/usr/local/lib`.

The concept of shared libraries is not exclusive to Linux. In Windows, for example, they are called DLL which stands for `dynamic linked libraries`.

## Configuration of Shared Library Paths
The references contained in dynamically linked programs are resolved by the dynamic linker (`ld.so` or `ld-linux.so`) when the program is run.

The `dynamic linker` searches for libraries in a number of directories. These directories are specified by the *library path*. The library path is configured in the `/etc` directory, namely in the file `/etc/ld.so.conf` and, more common nowadays, in files residing in the `/etc/ld.so.conf.d` directory.

The `ldconfig` command takes care of reading these config files, creating the aforementioned set of symbolic links that help to locate the individual libraries and finally fo updating the cache file `/etc/ld.so.cache`. Thus, `ldconfig` must be run every time configuration files are added or updated.

In order to use `ldconfig`, you must be the root user or use `sudo` to invoke it.

You can use the `LD_LIBRARY_PATH` environment variable to add new paths for shared libraries temporarily. For example, in order to add the library path `/usr/local/mylib` in the current shell session, you could type:

```shell
$ LD_LIBRARY_PATH=/usr/local/mylib
```

## Searching for the Dependencies of a Particular Executable
To look up the shared libraries required by a specific program, use the `ldd` command followed by the absolute path to the program. The output shows the path of the shared library file as well as the hexadecimal memory address at which it is loaded.

As an example:

```shell
$ ldd /usr/bin/git

linux-vdso.so.1 =>  (0x00007ffcbb310000)
libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f18241eb000)
libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f1823fd1000)
libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f1823db6000)
libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f1823b99000)
librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f1823991000)
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f18235c7000)
/lib64/ld-linux-x86-64.so.2 (0x00007f182445b000)
```



---
Concepts in this lesson:
-   ✅ `ldd`
-   ✅ `ldconfig`
-   ✅ `/etc/ld.so.conf`
-   ✅ `LD_LIBRARY_PATH`

---

###  ✏️ Guided Exercises
1. Divide the following shared library names into their parts: ✅
| Complete file name   | LIbrary name    | `so` suffix | Version Number |
| -------------------- | --------------- | ----------- | -------------- |
| linux-vdso.so.1      | linux-vdso      | so          | 1              |
| libprocps.so.6       | libprocps       | so          | 6              |
| libdl.so.2           | libdl           | so          | 2              |
| libc.so.6            | libc            | so          | 6              |
| libsystemd.so.0      | libsystemd      | so          | 0              |
| ld-linux-x86-64.so.2 | ld-linux-x86-64 | so          | 2              |
|                      |                 |             |                |

2. You have developed a piece of software and want to add a new shared library directory to your system (`opt/lib/mylib`). You write its absolute path in a file called `mylib.conf`.

✅ In what directory should you put this file? `/etc/ld.so.conf.d`

✅ What command should you run to make the changes fully effective? `ldconfig`

3. What command would you use to list the shared libraries required by `kill`?

✅ `ldd /usr/bin/kill`.