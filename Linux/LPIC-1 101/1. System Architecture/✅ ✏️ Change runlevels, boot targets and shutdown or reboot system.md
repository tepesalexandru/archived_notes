#linux #LPIC-1 

## SysVinit
A service manager based on the `SysVinit` standard will provide predefined sets of system states, called `runlevels`, and their corresponding service script files to be executed.

Runlevels are numbered `0` to `6`, being generally assigned to the following purposes:

- Runlevel 0 - System shutdown.
- Runlevel 1, s or single - Single user mode, without network and other non-essential capabilities (maintenance mode).
- Runlevel 2, 3, or 4 - Multi-user mode. Users can log in by console or network. Runlevels 2 and 4 are not often used.
- Runlevel 5 - Multi-user mode. It is equivalent to 3, plus the graphical mode login.
- Runlevel 6 - System restart.

The program responsible for managing runlevels and associated deamons/resources is `/sbin/init`.

During system initialization, the `init` program identifies the requested runlevel, defined by a kernel parameter or in the `/etc/inittab` file, and loads the associated scripts listed there for the given runlevel.

Every runlevel may have associated service files, usually scripts in the `/etc/init.d/` directory. As not all runlevels are equivalent through different Linux distributions,  a short description of the runlevel's purpose can also be found in SysV based distributions.

The syntax of the `/etc/inittab` file uses this format:

```
id:runlevels:action:process
```

The `id` is a generic name up to four characters in length used to identify the entry.
The `runlevels` entry is a list of runlevel numbers for which a specified action should be executed.
The `action` term defines how `init` will execute the process indicated by the term `process`.

### telinit
The `telinit q` command should be executed every time after the `/etc/inittab` file is modified. The argument `q` (or `Q`) tells init to reload its configuration. Such a step is important to avoid a system halt due to an incorrect configuration in `/etc/inittab`.

The command `runlevel` shows the current runlevel for the system. The command shows two values, the first is the previous runlevel and the second is the current runlevel.

The letter `N` in the output shows that the runlevel has not changed since last boot.

## systemd
Currently, systemd is the most widely used set of tools to manage system resources and services, which are referred to as *units* by systemd.

A `unit` consists of a name, a type and a correspondign configuration file. For example, the unit for an `httpd` server process (like the Apache web server) will be `httpd.service` on Red Hat based distributions and its configuration file will also be called `httpd.service` (on Debian based distributions this unit is named `apache2.service`).

The main command for controlling systemd units is `systemctl`. This command is used to execute all tasks regarding unit activation, deactivation, execution, interruption, monitoring, etc.

For a fictitious unit called `unit.service`, for example, the most common `systemctl` actions will be:

```shell
$ systemctl start unit.service # Starts unit
$ systemctl stop unit.service # Stops unit
$ systemctl restart unit.service # Restarts unit
$ systemctl status unit.service # Shows the state of the unit
$ systemctl is-active unit.service # Shows "active" or "inactive"
$ systemctl enable unit.service # Enables the unit, meaning it will load during system initialization
$ systemctl disable unit.service # Disables the unit, it won't load during system initialization
$ systemctl is-enabled # Verifies if unit starts with the system
```

The `systemctl` command can also control `system targets`.  The `multi-user.target` unit, for example, combines all units required by the multi-user system environment. It is similar to the runlevel number 3 in a system utilizing SysV.

Command `systemctl isolate multi-user.target` alternates between different targets. To manually alternate to target `multi-user`, use the following command:

```bash
$ systemctl isolate multi-user.target
```
A way to change the default target is to modify the symbolic link `/etc/systemd/system/default.target` so it points to the desired target. The redefinition of the link can be done with the `systemctl` command by itself:

```bash
$ systemctl set-default multi-user.target
```
Likewise, you can determine what your system's default boot target is with the following command:

```bash
$ systemctl get-default
graphical.target
```

## Upstart
The initialization scripts used by Upstart are located in the directory `/etc/init`. System services can be listed with command `initctl list`, which also shows the current state of the services and, if available, their PID number.

As an example:

```shell
$ initctl list

avahi-cups-reload stop/waiting
avahi-daemon start/running, process 1123
mountall-net stop/waiting
mountnfs-bootclean.sh start/running
nmbd start/running, process 3085
passwd stop/waiting
rc stop/waiting
rsyslog start/running, process 1095
tty4 start/running, process 1761
udev start/running, process 1073
upstart-udev-bridge start/running, process 1066
console-setup stop/waiting
irqbalance start/running, process 1842
plymouth-log stop/waiting
smbd start/running, process 1457
tty5 start/running, process 1764
failsafe stop/waiting
```

Every Upstart action has its own independent command. For example, command `start` can be used to initiate a sixth virtual terminal:

```shell
$ start tty6
```

The current state of a resource can be verified with command `status`:

```shell
$ status tty6

tty6 start/running, process 3282
```

And the interruption of a service is done with the command `stop`:

```shell
stop tty6
```

Upstart does not use the `/etc/inittab` file to define runlevels, but the legacy commands `runlevel` and `telinit` can still be used to verify and alternate between runlevels.

## Shutdown and Restart
The `shutdown` command is used in order to shutdown the system. It also adds extra functions to the power off process: it automatically notifies all logged-in users with a warning message in their shell session and new logins are prevented.

Command `shutdown` acts as an intermediary to SysV or systemd procedures, that is, it executed the requested action by calling the corresponding action in their services manager adopted by the system.

After `shutdown` is executed, all processed receive the `SIGTERM` signal, followed by the `SIGKILL` signal, then the system shuts down or changes runlevels.

By default, the system will alternate to runlevel 1 (single user mode) after running the `shutdown` command.

To change the default options for `shutdown`, the command should be executed with the following syntax:

```shell
$ shutdown [option] time [message]
```

Only the `time` parameter is required. The `time` parameter defines when the requested action will be executed, accepting the following formats:

- `hh:mm` - time as hour and minutes
- `+m` - how many minutes to wait before execution
- `now` or `+0` - immediate execution

The `message` parameter is the warning text sent to all terminal sessions of logged-in users.

The `systemctl` command can also be used to turn off or to restart the machine in systems employing systemd. To restart the system, the command `systemctl reboot` should be used.

To turn off the system, the command `systemctl poweroff` should be used. Both commands require root privileges to run, as ordinary users cannot perform such procedures.

Examples:

```shell
$ systemctl poweroff # Shuts the system down
$ systemctl reboot # Restarts the system
```

In order to cancel a system shutdown / reboot, use the following command:

```shell
$ shutdown -c
```
Similar to what the `shutdown` command does when powering off or restarting the system, the `wall` command is able to send a message to terminal sessions of all logged-in users.

To do so, the system administrator only needs to provide a file or directly write the message as a paramter to the command `wall`.

`wall` is short for "**w**rite a message to **all** users".

---

### Concepts in this lesson:
-   ✅ `/etc/inittab`
-   ✅ `shutdown`
-   ✅ `init`
-   ✅ `/etc/init.d/`
-   ✅ `telinit`
-   ✅ `systemd`
-   ✅ `systemctl`
-   ✅ `/etc/systemd/`
-   ✅ `wall`

---

###  ✏️ Guided Exercises
1. How could the `telinit` command be used to reboot the system?

✅ By using `telinit 6`.

2. What will happen to the services related to the file `/etc/rc1.d/K90network` when the system enters runlevel 1?

✅ Due to the letter `K` in the beginning of the file name, the related services will be stopped.

3. Using command `systemctl`, how could a user verify if the unit `sshd.service` is running?

✅ By using the command `systmctl status sshd.service` or `systemctl is-active sshd.service`.

4. In a systemd based system, what command must be executed to enable activation of the unit `sshd.service` during system initialization?

✅ The command is `systmctl enable sshd.service`, exeucted by `root`.