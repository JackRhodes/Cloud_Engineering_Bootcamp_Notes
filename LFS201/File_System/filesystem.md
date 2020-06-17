The standard file system is shared between all distros.
 [PDF here explaining the standard](fhs-3.0.pdf)

Any directories that are not mentioned in the following image are usually OS specific:
[Image](Main-Directories.png)


# Core Folders

The root file system needs to contain all files to enable a system to boot. Then any additonal files can be from different shares.

## /Bin

Required programs. This includes some of the most basic shell commands such as `ls` , `echo` and `rm`. These can be run by any privilleged or unprvilleged user. Example of core programs on my laptop:

[Core Files](bin-on-my-laptop.png)


## /Boot
Files that are needed to actually boot the system are found here.


* *vmlinuz*: The compressed linux kernel
* *initramfs*: The initial Ram file system that is mounted before the real root file system is available.
* *config* : Used in configuring kernel compilation
* *System.map* : Kernol symbol table. I believe this is similar to a .pdb but for the Kernel

In older versions of Linux the boot fodler didn't exist and everything was just stored in the root

[Boot](boot-on-my-laptop.png)

## /Dev
This contains devices connected to the system. You can find stuff such as the WiFi card, any usb connected devices and any internal devices. Modern systems use `udev` which basically adds virtual directories here when devices are plugged in. On an unmounted system it'd be empty.

[Dev](dev-on-my-laptop.png)

## /Etc

Local configuration files that get run at startup. For example you can set a bunch of config data here, such as hostnames in /etc/hosts, or startup services in /etc/sytemmd. It's the one stop shop of system wide configuration. 


[Dev](etc-on-my-laptop.png)

## /Home
The home directories of any users on the device. Stores all user specific data that is shared across device. Think of it as the C:/Users folder in Windows.

Worth remembering is that the Linux file system isn't ponting to their actual locaiton on disk, so a users home folder could be sitting anywhere and just mounted to be in /home.

## /lib and /lib64

The libraries needed to execute binaries in /bin and /sbin.

## /media
Used to show mounted filesystems like usb sticks.

On modern systems `/run/media/[username]` is used instead.

## /mnt
Used for mounted hardrive and NAS

## /opt
Used for installing self-contained apps that don't want their files to be put everywhere. Having them here makes it easier to add / remove a program

In practice, you will generally use a package manager, but for any installations outside of a package manager then this can be useful.

## /proc
Used to display psudo-files that are in memory in a location on the file system. 

Important pseudo-files, including /proc/interrupts, /proc/meminfo, /proc/mounts, and /proc/partitions, provide an up-to-the-moment glimpse of the system's hardware.

Others, like /proc/filesystems and the /proc/sys/ directory, provide system configuration information and interfaces.

## /sys

Mount point for the sysfs pseudo-file system.

Sysfs is used to gather information about the system. It's basically a modern extension of /proc with stricted standards, such as requiring files to be one line long

## /root
The root users home directory

## /sbin 
Binaries essential for booting, restoring, recovering and/or repairing. Some distributions choose to standardise this with /bin and have one directory with links to this directory to mainatain the fhs standard.

## /srv
Used to store data files for some services. It's not really enforced properly. 

## /tmp
A place to store temporary files. Ubuntu removes these on reboot. Some distributions actually store everything in here in memory.

## /usr
Does not need to reside in the same partiton as the root directory since it isn't used on startup. It can be shared among many hosts if needed. It should contain readonly data, for example /usr/share/man can store manual pages.

## /var
Volatile file storage, used for data that frequently changes, such as log files.

It is often used as a mount for things such as mailboxes, ftp or websites.

/var/www is found for website files for example
/var/log can contain logs

[My Logs](logs-on-my-laptop.png)

Common subfolders in /var/:
[var subdirectories](var-directories.png)

## /run
Not formally in the FHS spec.

Store transient files at runtime which may need to preserved, but should be re-created upon reboot.