#linux #LPIC-1 

### Communication channels
Standard Linux processes have three communication channels opened by default:
1. the `standard input` channel (`stdin`)
2. the `standard output` channel (`stdout`)
3. the `standard error` channel (`stderr`)

The `numerical file descriptors` assigned to these channels are:
- `0` for `stdin`
- `1` for `stdout`
- `2` for `stderr`

Communication channels are also accessible through the special devices `/dev/stdin`, `/dev/stdout` and `/dev/stderr`.

In a standard shell session, the keyboard is defined as the `stdin` and the monitor screen is defined as the `stdout` and `stderr`.

The bash shell has the ability to `reassign` the communication channels when loading a program. It allows, for example, to override the screen as the standard output and use a file in the local filesystem as stdout.

### Redirects
The reassignment of a channel's file descriptor in the shell is called a `redirect`.

A `redirect` is defined by a special character within the command line (usually `>`).

For instance, to redirect the standard output of a process to a file, the `>` symbol is positioned at the end of the command and followed by the path to the file that will receive the redirected output:

```bash
cat /proc/cpuinfo > /tmp/cpu.txt
```
By default, only the content coming to `stdout` is redirected. Therefore, using `>` is equivalent to use `1>`. To capture the content of `stderr`, the redirect `2>` should be used instead.

Both `stdout` and `stderr` are redirected to the same target with `&>` or `>&`, for instance:

```bash
cat /proc/cpuinfo &> /tmp/cpu.txt
```
To just discard the output of a command, its content can be redirected to the special file `/dev/null`.

For example `>log.txt 2>/dev/null` saves the contents of `stdout` in the file `log.txt` and discards the `stderr`.

The file `/dev/null` is writable by any user but no data can be recovered from it, as it is not stored anywhere.

Data can be appended to a file using the `>>` symbol.

The data source of the `stdin` process can be reassigned as well, using the `<` symbol.

### Here Document and Here String
Another way to redirect input involve the `Here document` and `Here string` methods.

The `Here document` redirect allows to type multi-line text that will be used as the redirected content, and is represtend by the symbol `<<`.

The `Here string` method is much like the `Here document`, but for a single line, and is represtented by the symbol `<<<`.

A few examples:

```bash
wc -c <<< "Hi"
3

wc -c <<EOF
> How are you?
> Good, how are you?
> Good!
> EOF
38
```

---
Key knowledge areas
• Redirecting standard input, standard output and standard error.
• Pipe the output of one command to the input of another command.
• Use the output of one command as arguments to another command.
• Send output to both stdout and a file.

Partial list of the used files, terms and utilities (?)
-  `tee`
-  `xargs`