#linux #LPIC-1 

## Introduction
A great way to get started with text streams is by reading the user input from the command line. You can do this using the `cat` command, followed by the string you want to read. After you're done with the cat command, simply exit by pressing CTRL + C and you it will output the text you've written in the command line.

The naming of the command comes from "concatenate", because it concatenes the I/O Stream of the cli to the file system.

```shell
$ cat
Hello there!
How are you today?
^C

# Outputs:
# Hello there!
# How are you today?
```

This command also let's you create a new text file with the content from the user input collected from the terminal.

```shell
$ cat > hello.txt
Hello there!

# Creates the file "hello.txt" with the content "Hello there!"
```

Also, you can display the contents of a file using the cat command:

```shell
$ cat hello.txt

# Outputs: Hello there!
```

We can use pipes (represented by the symbol `|`) to redirect the output of one program to another program. Let us find where the word "this" found:

```shell
$ cat mytextfile | grep this

I hope cat is storing this to mytextfile as I redirected the output
I will hit ctrl+c now and check this
```

## Processing Text Streams
### Reading a Compressed File
You can compress a file by using the `gzip` command and specifying which file you'd like to compress. This command will remove the original file.

```shell
$ gzip hello.txt

# Creates hello.txt.gz
```

And in order to view the contents of a gzipped compressed file, you can use the `zcat` command:

```shell
$ zcat hello.txt.gz

Hello!
```

## Viewing a File in a Pager
You know `cat` concatenates a file to the standard output (once a file is provided after the command). 

The file `/var/log/syslog` is where your Linux system stores everything important going on in your system. Using the `sudo` ("superadmin do") command to elevate privileges so as to be able to read the `/var/log/syslog` file:

```shell
$ sudo cat /var/log/syslog
```

The output of this command will be hundreds of lines. You can pipe the output to the command program `less` so the results will be `paginated`. By using `less` you can use the arrow keys to navigate through the output and also use `vi` like commands to navigate and search throughout the text.

However, rather than pipe the `cat` command into a pagination program it is more pragmatic to just use the pagination program directly:

```shell
$ sudo less /var/log/syslog
```

## Getting a Portion of a Text File
If only the start or end of a file needs to be reviewed, there are other methods available. The command `head` is used to read the `first` ten lines of a file by default, and the command `tail` is used to read the `last` ten lines of a file by default. Examples below:

```shell
$ sudo head /var/log/syslog # Outputs the first ten lines
$ sudo tail /var/log/syslog # Outputs the last ten lines
```

You can also pipe the output of the `head` command to the `nl` command, which will display the number of lines of text streamed into the command:

```shell
$ sudo head /var/log/syslog | nl

1 ...
2 ...
3 ...
4 ...
# etc.
```

We can also use the `wc` command, which by default will count the number of words within a document, and using the `-l` switch to print out the number of lines of text that the command has read:

```shell
$ sudo tail /var/log/syslog | wc -l

10
```

If you need to customize the number of lines that the `head` or `tail` command will output, you can use the `-n` parameter and specify the number of lines you'd like to see. Example:

```shell
$ sudo tail -n 5 /var/log/syslog # Will display the last 5 lines
$ sudo head -n 12 /var/log/syslog # Will display the first 12 lines
```

## The Basics of `sed` , the Stream Editor
Another useful parameter to the `grep` command is the `-v` parameter, which allows us to filter file lines which do *not* contain a certain word. For example:

```shell
$ zcat foo.txt.gz | grep -v hello

# Outputs all file lines that do not contain the word "hello"
```

Most of what can be done with `grep` can also be done with `sed`, the `stream editor` for filtering and transforming text. 

For example, hwere we can display all lines that contain the word "cat" in the "foo.txt" file:

```shell
$ sed -n /cat/p < foo.txt

# Output...
```

The less-than sign `<` is used to direct the contents of the file "foo.txt" into the `sed` command. The word enclosed between slashes (i.e. `/cat/`) is the term we are searching for. The option `-n` instructs `sed` to product no output (unless the ones later instructed by the `p` command).

## Ensuring Data Integrity
We have demonstrated how easy it is to manipulate files in Linux. There are times where you may wish to distribute a file to someone else, and you want to be sure that the recipient ends up with a `true copy` of the original file.

A very common use of this technique is practiced when Linux distributions servers host downloadable CD or DVD images of their software along with files that contain the calculated checksum values of those disc images. Here is an example listing from a Debian download mirror:

```
[PARENTDIR] Parent Directory                                      -
[SUM]       MD5SUMS                              2019-09-08 17:46 274
[CRT]       MD5SUMS.sign                         2019-09-08 17:52 833
[SUM]       SHA1SUMS                             2019-09-08 17:46 306
[CRT]       SHA1SUMS.sign                        2019-09-08 17:52 833
[SUM]       SHA256SUMS                           2019-09-08 17:46 402
[CRT]       SHA256SUMS.sign                      2019-09-08 17:52 833
[SUM]       SHA512SUMS                           2019-09-08 17:46 658
[CRT]       SHA512SUMS.sign                      2019-09-08 17:52 833
[ISO]       debian-10.1.0-amd64-netinst.iso      2019-09-08 04:37 335M
[ISO]       debian-10.1.0-amd64-xfce-CD-1.iso    2019-09-08 04:38 641M
[ISO]       debian-edu-10.1.0-amd64-netinst.iso  2019-09-08 04:38 405M
[ISO]       debian-mac-10.1.0-amd64-netinst.iso  2019-09-08 04:38 334M
```

A `checksum` is a value derived from a mathematical computation, based on the cryptographic hash function, against a file. There are different types of cryptographic hash functions that vary in strength. Some examples are `md5sum`, `sha256sum` and `sha512sum`.

Once you download a file (for example, the `debian-10.1.0-amd64-netinst.iso` image) you would then compare the checksum of the file that was downloaded against a checksum value that was provided for you.

Here is an example to illustrate the point:

```bash
sha256sum hello.txt
98ea6e4f216f2fb4b69fff9b3a44842c38686ca685f3f55dc48c5d3fb1107be4  hello.txt
```
The above command gives the SHA 256 Sum of the `hello.txt` file. We can save that sum to a file named `sha256.txt`:

```bash
sha256 sum hello.txt > sha256.txt
```

Then, we can check the `hello.txt` file by verifying the SHA 256:

```bash
sha256sum -c sha256.txt
hello.txt: OK
```

### Looking deeper into files
The octal dump (`od`) command is often used for debugging applications and various failes.

By itself, the `od` command will just list out a file's contents in octal format:

```bash
od hello.txt
0000000 064550 000012
0000003

# Or, in HEX format
od -x hello.txt
0000000 6968 000a
0000003
```
The `od` command can also show characters that would normally not be visible in a file, such as an `newline` entry, with the `-c` option:

```bash
od -c hello.txt
0000000   h   i  \n
0000003
```

---

Concepts in this lesson:
-   ✅ `bzcat`
-   ✅ `cat`
-   ✅ `cut`
-   ✅ `head`
-   ✅ `less`
-   ✅ `md5sum`
-   ✅ `nl`
-   ✅ `od`
-   ✅ `paste`
-   ✅ `sed`
-   ✅ `sha256sum`
-   ✅ `sha512sum`
-   ✅ `sort`
-   ✅ `split`
-   ✅ `tail`
-   ✅ `tr`
-   ✅ `uniq`
-   ✅ `wc`
-   ✅ `xzcat`
-   ✅ `zcat`