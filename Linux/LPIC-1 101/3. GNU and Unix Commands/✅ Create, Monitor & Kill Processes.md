#linux #LPIC-1 

## Introduction
Every time a command is invoked in Linux, one or more processes are started. A great Linux administrator not only needs to create processes, but also be able to keep track of them and send them different types of `signals` if and when required.

## Jobs
`Jobs` are processes that have been started interactively through a terminal, sent to the background and have not yet finished execution.

You can see all active jobs with the `jobs` command:

```shell
$ jobs

[1]+  Stopped                 sleep 60
```

If you also provide the `-l` option, it will also display the PID right before the status:

```shell
$ jobs -l

[1]+  1114 Stopped                 sleep 60
```

### Job Specification
In order to be able to act on a specific job, you need a job specification. This can be a number, a string pattern, or directly selecting the last or previous job.

A few examples:

```shell
$ jobs %n // Selects all jobs whose id is n
$ jobs %str // Selects all jobs starting with str
$ jobs %?str // Selects all jobs ending with str
$ jobs %+ // Selects the current job
$ jobs %- // Selects the previous job
```

### Job Status: Suspension, Foreground and Background
You can take a job to the foreground using the `fg` ("foreground") command:

```shell
$ fg %1 // 1 is the process id
```

Bringing a process to foreground means that now we can wait until it is finished, stop it again with `CTRL + Z` or terminate it with `CTRL + C`.

You can take a job to the background using the `bg` ("background") command:

```shell
$ bg %1

[1]+ sleep 60 &
```

The `&` symbol denotes that the job has been sent to the background. As a matter of fact, you can use the ampersand to start a process directly in the background:

```shell
$ sleep 60 & // will start in the background
```

A job is terminated when it receives the `SIGTERM` signal. The command `kill` sends this signal to a specific process. Here is an example:

```shell
$ kill %1 // terminates the process with id 1
```

### Detached Jobs: `nohup`
The jobs we have seen in the previous sections were all attached to the session of the user who invoked them. That means that if the session is terminated, the jobs are gone.

However, it is possible to detach jobs from the current session and have them run even after the session is closed. This is achieved with the `nohup` ("no hangup") command.

The syntax is as follows:

```bash
nohup COMMAND &
```
The `&` symbol sends the process into the background and frees up the terminal you are working at.


## Process Monitoring
A process or task is an instance of a running program. Thus, you create new processes every time you type in commands into the terminal.

The `watch` command executes a program periodically (2 seconds by default) and allows us to watch the program's output change over time.

For instance:

```bash
watch uptime # how much the system has been on
watch free # memory
watch -n 5 free # watch memory every 5 seconds
```

The command runs until interrupted so we would have to stop it with `Ctrl + C`.

### Sending Signals to Processes: `kill`
Every single process has a unique process identifier or `PID` for short.

You can find the PID of a process with the `pgrep` command:

```bash
pgrep sleep
1201
```
Similar to `pgrep`, the `pkill` command kills a process based on its name:

```bash
pkill sleep
[1]+ Terminated sleep 60
```

To kill all instances of the same process, the `killall` command can be used:

```bash
killall sleep
[1]- Terminatedsleep 60
[2]+ Terminatedsleep 70
```
To have `kill` work in a similar way to `pkill` or `killall` (and save ourselves the commands to find out PIDs first), we can use command substitution:

```bash
kill -1 $(prgrep sleep)
```

### `top` and `ps`
When it comes to process monitoring, two invaluable tools are `top` and `ps`.

Whilst the former produces output dynamically, the latter does it statically. In any case, both are excellent utilities to have a comprehensive view of all processes in the system.

The `top` command output is divided into two areas: the `summary area` and the `task area`.

The `ps` command reports information about processes, and can even target a specific one.

The syntax for the command is:

```bash
ps # show all PIDs
ps -p 811 # show information about process with PID 811
```
To get the best of both worlds between `ps` and `top`, we can use the command `ps aux` to get processes from all shells (not only the current one).

```bash
ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0 169580 14136 ?        Ss   07:38   0:01 /sbin/init sp
root           2  0.0  0.0      0     0 ?        S    07:38   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   07:38   0:00 [rcu_gp]
root           4  0.0  0.0      0     0 ?        I<   07:38   0:00 [rcu_par_gp]
root           5  0.0  0.0      0     0 ?        I<   07:38   0:00 [slub_flushwq
root           6  0.0  0.0      0     0 ?        I<   07:38   0:00 [netns]
```
### Terminal Multiplexers
In electronics, a *multiplexer* (or *mux*) is a device that allows for multiple inputs to be connected to a single output.

Thus, a terminal multiplexer gives us the ability to switch between different inputs as required.

The `screen` and `tmux` commands share a series of common features.

#### GNU Screen
In the early days of Unix (1970s - 80s) computers basically consisted of terminals connected to a central computer. That was all, no multiple windows or tabs. That was the reason behind the creation of GNU Screen in 1987: emulate multiple independent VT100 screens on a single physical machine.

You can get started by installing `screen` and running the command itself.

```bash
sudo apt install screen
screen # Starts the GNU Screen
```
### `tmux`

`tmux` was released in 2007.  Just like `screen`, you can get started in the same way:

```bash
sudo apt install tmux
tmux # Startes tmux
```

---

Concepts in this lesson:
-   ✅ `&`
-   ✅ `bg`
-   ✅ `fg`
-   ✅ `jobs`
-   ✅ `kill`
-   ✅ `nohup`
-   ✅ `ps`
-   ✅ `top`
-   ✅ `free`
-   ✅ `uptime`
-   ✅ `pgrep`
-   ✅ `pkill`
-   ✅ `killall`
-   ✅  `watch`
-   ✅ `screen`
-   ✅ `tmux`