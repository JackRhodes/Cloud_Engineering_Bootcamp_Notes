A process is an instance of a program in execution. It may be in a number of different states, such as running or sleeping. Every process has a 

* pid (Process ID), 
* ppid (Parent Process ID)
* pgid (Process Group Id)

init is usually the first user process run on a system

If the parent process dies before the child, the ppid of the child is set to 1; i.e., the process is adopted by init

All processes have the following attributes:

* The program being executed
* Context (state)
* Permissions
* Associated resources.

[Process States](process-states.png)


Execution Modes:
* User mode: everything is confined to that user, the msot common way of a process being ran
* Kernel Mode: The process has access to everything on the device

## Daemons
A background service

* Daemons can be quite efficient because they only operate when needed.
* Many daemons are started at boot time.
* Daemon names often (but not always) end with d.
    Some examples include httpd and systemd-udevd.
* Daemons may respond to external events (systemd-udevd) or elapsed time (crond).
* Daemons generally have no controlling terminal and no standard input/output devices.
* Daemons sometimes provide better security control.

When using SysVinit, scripts in the /etc/init.d directory start various system


## ulimit

Ulimit is used to set the resource limits associated with a process. This is used to prevent a process from exhausting all of a systems resources.

This can be configuyred globally for users by modifying: /etc/security/limits.conf



