#linux 

Let's learn some basic commands for Linux in order to help us with DevOps tasks.

- `mkdir/rmdir` - make/remove an empty directory

```shell
# Create directory "a"
mkdir a

# Create nested directories b and c, b being the parent
mkdir b/c -p

# Delete the EMPTY directory "a"
rmdir a
```

- `touch` - if the file exists, update the modification time to "now", otherwise it will create it.

```shell
# If "post.txt" exists, it updates the last modified time to now
touch post.txt 

# If "article.txt"
touch article.txt
```

- `ls` - list the information about files in a directory

```shell
# Lists the files in the current directory
ls

# Lists file details
ls -l

# Lists file names (including hidden files)
ls -a

# Lists file and sorts them by size in descending order
ls -laS

# Lists file of the "/example" directory
ls /example
```

- `clear` - clears your terminal screen

```shell
# CLears the terminal screen
clear
```

- `cd` - navigate through files and directories

```shell
cd .. # Go up one directory
cd # Go to the home folder
cd - # Move to the previous folder
```

More can be found here: https://www.hostinger.com/tutorials/linux-commands
Linux Certification: https://www.lpi.org/our-certifications/exam-101-objectives
https://www.lpi.org/our-certifications/lpic-1-overview

https://learning.lpi.org/en/learning-materials/102-500/109/109.1/109.1_01/