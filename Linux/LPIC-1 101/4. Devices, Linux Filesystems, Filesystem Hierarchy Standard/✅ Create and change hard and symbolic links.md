#linux #LPIC-1 

### Types of Link
On Linux, some files get a special treatment because of the place they are stored in, such as temporary files, or the way they interact with the filesystem, like links.

There are two types of `link` files in Linux:
1. `Symbolic Links` - also called *soft links*, they point to the path of another file.
2. `Hard Links` - They are files that point to the same `inode` on the disk.

An `inode` is a data structure that stores attributes for an object (like a file or directory) on a filesystem. Among those attributes are permissions, ownership and on which block of the disk the data for the object is stored. The name comes from "*index node*".

### Hard Links
To create a new hard link in Linux, use the `ln` command:

```bash
ln TARGET LINK_NAME
```
You can view the `inode` of a file by using the following command:

```bash
ls -li
total 224
3806696 -r--r--r-- 2 carol carol 111702 Jun7 10:13 hardlink
3806696 -r--r--r-- 2 carol carol 111702 Jun7 10:13 target.txt
```
In the example above, both files have the same `inode` (3806696). All files also have a `link count`, which for the example above is `2` (how many files point to that `inode`).

Since hard links are trated as regular files, they can be deleted with `rm`, or moved around with `mv`, without breaking the link.

### Symbolic Links
To create a new symbolic link in Linux, use the following command:

```bash
ln -s TARGET LINK_NAME
```
Contrary to hard links, you can create symbolic links to *directories*.

You can identify symbolic links with the following command:

```bash
ls -lh
total 112K
-rw-r--r-- 1 carol carol 110K Jun7 10:13 target.txt
lrwxrwxrwx 1 carol carol7 10:14 softlink -> target.txt # This is the symbolic link
```
The first character on the permissions is `l`, indicating that its a symbolic link.

Like hard links, symbolic links can be moved around freely and also removed. You only need to be careful if the path of the symbolic link was defined as `relative`.


---

Key knowledge areas
• Create links.
• Identify hard and/or soft links.
• Copying versus linking files.
• Use links to support system administration tasks.
Partial list of the used files, terms and utilities
- ✅ `ln`
- ✅ `ls`