#linux #LPIC-1 

Operating systems able to run more than one process at the same time are called multi-tasking or multi-processing systems.

Only one process at a time can control the CPU. However, most process activities are `system calls`, that is, the running process transfers CPU control to an operating system's process so it performs the requested operation.

### The Linux Scheduler
Linux, as a `preemptive multi-processing` operating system, implements a `scheduler` that organizes the `process queue`.

Every process has two predicates that intervene on its scheduling: the `scheduling policy` and the `scheduling priority`.

There are two main types of scheduling policies: `real-time policies` and `normal policies`.

Processes under a `real-time` policy are scheduled by their priority values directly. If a more important process becomes ready to run, a less important process is preempted and the higher priority process takes control of the CPU. A lower priority process wil gain CPU control only if higher priority processes are idle or waiting for hardware response.

Normal processes usually have the same priority value, but normal policies can define execution priority rules using another process predicate: the `nice` value.

To avoid confusion with the dynamic priorities derived from nice values, scheduling priorities are usually called `static` scheduling priorities.

### Reading Priorities
Linux reserves `static priorities` ranging from `0 to 99` for `real-time` processes and `normal processes` are assigned to `static priorities` ranging from `100 to 139`, meaning that there are 39 different priority levels for a normal processes.

Lower values mean higher priority.

The static priority of an active process can be found in the `sched` file, located in its respective directory inside the `/proc` filesystem:

```bash
grep ^prio /proc/1/sched
prio: 120
```

The standard priority for normal processes is 120, so that it can be decreased to 100 or increased to 139. The priorities of all running processes can be verified with the command `ps -Al` or `ps -el`:

```bash
ps -el
F S   UID     PID    PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0       1       0  0  80   0 - 42448 -      ?        00:00:02 systemd
1 S     0       2       0  0  80   0 -     0 -      ?        00:00:00 kthreadd
1 I     0       3       2  0  60 -20 -     0 -      ?        00:00:00 rcu_gp
1 I     0       4       2  0  60 -20 -     0 -      ?        00:00:00 rcu_par_gp
1 I     0       5       2  0  60 -20 -     0 -      ?        00:00:00 slub_flush
1 I     0       6       2  0  60 -20 -     0 -      ?        00:00:00 netns
1 I     0       8       2  0  60 -20 -     0 -      ?        00:00:00 kworker/0:
1 I     0      10       2  0  60 -20 -     0 -      ?        00:00:00 mm_percpu_
1 I     0      11       2  0  80   0 -     0 -      ?        00:00:00 rcu_tasks_
1 I     0      12       2  0  80   0 -     0 -      ?        00:00:00 rcu_tasks_
1 I     0      13       2  0  80   0 -     0 -      ?        00:00:00 rcu_tasks_
1 S     0      14       2  0  80   0 -     0 -      ?        00:00:00 ksoftirqd/
1 I     0      15       2  0  80   0 -     0 -      ?        00:00:08 rcu_preemp
1 S     0      16       2  0 -40   - -     0 -      ?        00:00:00 migration/
1 S     0      17       2  0   9   - -     0 -      ?        00:00:00 idle_injec
```

The `PRI` column indicates the static priority assigned by the kernel.

However, due to historical reasons, priorities displayed by `ps` range from `-40 to 99` by default, so the actual priority is obtained by adding 40 to it.

### Process Niceness
Every normal process begins with a default nice value of 0 (priority 120). The `nice` name comes from the idea that "nicer" processes allow other processes to run before them in a particular execution queue.

Nice numbers range from -20 (less nice, high priority) to 19 (more nice, low priority).

The `NI` column in the `ps` output indicates the `nice` number.

The command `renice` can be used to change the priority of a running process. The option `-p` indicates the PID number of the target process. For example:

```bash
renice -10 -p 2164
2164 (process ID) old priority 0, new priority -10
```

The options `-g` and `-u` are used to modify all the processes of a specific group or user, respectively.

For instance, by using the following command, the niceness of processes owned by users of the group `users` will be raised by five:

```bash
renice +5 -g users
```
The niceness of a process can also be changed with the `top` command, by pressing `r` and then the PID number of the process

---
Concepts in this lesson:
- ✅ `nice`
- ✅ `ps`
- ✅ `renice`
- ✅ `top`