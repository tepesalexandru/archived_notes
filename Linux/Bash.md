```bash
if [ -z "$1" ] # checks if the first argument is set
then
    echo "One for you, one for me."
else
    echo "One for $1, one for me."
fi
```

```bash
$# # This returns the number of arguments passed to the script
```

---

## Introduction
What is Bash? Bash stands for "Bourne Again Shell", and is a tool for managing Linux machines.

A `shell` is a program that commands the operating system to perform actions.

You can write commands directly into the console, or write a `script` to run a batch of them.

One reason for Bash's success is its simplicity. It follows the design philosophy behind Unix:
- Programs do one thing and do it well
- Programs work together
- Programs use text streams as the universal interface

## Fundamentals
The universal syntax for a Bash `command` is the following:

```bash
command [options] [arguments]
```

An example of a bash command is:

```bash
ls -a /etc
ls /etc
ls
```

All three commands from above are valid. This is because `options` and `arguments` are optional for the `ls` command.