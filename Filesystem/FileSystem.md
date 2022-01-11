# Filesystem

## List of dir structure

### 1) / Root Start of entire file system hierarchy

```text
Only root user have write permission under this directory
```

### 2) /bin : Essential command binaries for single-user mode; for all users, e.g., cat, ls, cp

```text
Binary files are the files which contain compiled source code (or machine code)

Commands needed during bootup that might be used by normal users (probably after bootup).

Commands used by all the users of the system are located here e.g. ps, ls, ping, grep, cp

According to the FHS the /bin directory should contain /bin/cat and /bin/date (among others).

The ‘/bin’ directory doesn’t contain directories.

```

### 3) /boot : Boot loader files, e.g., kernels, initrd 

```text
This directory contains everything required for the boot process.

/boot directory stores data that is used before the kernel begins executing user-mode program.

Kernel initrd, vmlinux, grub files are located under /boot

Example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic

> /boot/boot.0300
>> Backup master boot record.

>/boot/boot.b
>> This is installed as the basic boot sector. In the case of most modern distributions it is actually a symbolic link to one of four files /boot/boot-bmp.b, /boot/boot-menu.b, /boot/boot-text.b, /boot/boot-compat.b which allow a user to change the boot-up schema
>> To change the actual 'boot-logo' you can either use utilities such as fblogo or the more refined bootsplash.

> /boot/config-kernel-version
>> Installed kernel configuration. This file is most useful when compiling kernels on other systems or device modules

> /boot/map
>> Contains the location of the kernel.

> /boot/vmlinuz, /boot/vmlinuz-kernel-version
>> Normally the kernel or symbolic link to the kernel

> /boot/grub
>> This subdirectory contains the GRUB configuration files including boot-up images and sounds

> /boot/grub/device.map
>> Maps devices in /dev to those used by grub. For example, (/dev/fd0) is represented by /dev/fd0 and (hd0, 4) is referenced by /dev/hda5.

> /boot/grub/grub.conf, /boot/grub/menu.lst
>> Grub configuration file.

> /boot/grub/messages
>> Grub boot-up welcome message.

```

### 4) /dev : Essential device files, e.g., /dev/null

```text
Consists of files that represent devices that are attached to the local system

It highlights one important aspect of the Linux filesystem - everything is a file or a directory

Example: /dev/tty1, /dev/usbmon0

/dev/cdrom and /dev/fd0 represent your CD-ROM drive and your floppy drive

Take /dev/dsp, for instance. This file represents your speaker device. 
Any data written to this file will be re-directed to your speaker. 
If you try 'cat /boot/vmlinuz > /dev/dsp' (on a properly configured system) you should hear some sound on the speaker. 
That's the sound of your kernel

Sending data to and reading from /dev/ttyS0 will allow you to communicate with a device attached there - for instance, your modem

These include terminal devices, usb, or any device attached to the system.

These are not regular files that a user can read and write to.

These files are called devices files or special files.

In general, 'block devices' are devices that store or hold data, 'character devices' can be thought of as devices that transmit or transfer data

For example hard drives and CD-ROM drives are all block devices
Serial ports, mouse and parallel printer ports are all character devices

Some common device files
> /dev/hda
>> /dev/hda is the master IDE drive on the primary IDE controller. 
/dev/hdb the slave drive on the primary controller. /dev/hdc , and /dev/hdd are the master and slave devices on the secondary controller respectively.

> /dev/null
>> The bit bucket. A black hole where you can send data for it never to be seen again. Anything sent to /dev/null will disappear

> /dev/zero
>> This is a simple way of getting many 0s. Every time you read from this device it will return 0. 
This can be useful sometimes, for example when you want a file of fixed length but don't really care what it contains. 

> /dev/ttyS0 (First communications port, COM1)
>> First serial port (mice, modems).

> /dev/psaux (PS/2)
>> PS/2 mouse connection (mice, keyboards).

> /dev/dsp (First audio device)
>>  Sound cards may use a dedicated DSP chip, or may implement the functions with a number of discrete devices

> /dev/usb (USB Devices)
>> This subdirectory contains most of the USB device nodes.

> /dev/sda (C:\, SCSI device)
>> First SCSI device (HDD, Memory Sticks, external mass storage devices such as CD-ROM drives on laptops, etc).


/dev/random is a Pseudo-Device does’t correspond to hardware devices

/dev/random is a function that generates random data

```

### 5) /etc : Host-specific system-wide configuration files

```text
Contains configuration files required by all programs.
This also contains startup and shutdown shell scripts used to start/stop individual programs.
Example: /etc/resolv.conf, /etc/logrotate.conf.

> /etc/rc or /etc/rc.d or /etc/rc?.d
>> Scripts or directories of scripts to run at startup or when changing the run level

> /etc/passwd
>> The user database, with fields username, real name, home directory, and other information about each user. 

> /etc/shadow
>> /etc/shadow is an encrypted file the holds user passwords

> /etc/fstab
>> Lists the filesystems mounted automatically at startup by the mount -a command (in /etc/rc or equivalent startup file)

> /etc/group'
>> Similar to /etc/passwd, but describes groups instead of users

> /etc/inittab
>> Configuration file for init

> /etc/issue
>> Output by getty before the login prompt. Usually contains a short description or welcoming message to the system. Contents are up to the system administrator

> /etc/magic
>> The configuration file for file. Contains the descriptions of various file formats based on which file guesses the type of the file.

> /etc/motd
>> The message of the day, automatically output after a successful login. Contents are up to the system administrator. 
Often used for getting information to every user, such as warnings about planned downtimes.

> /etc/profile, /etc/bash.rc, /etc/csh.cshrc
>> Files executed at login or startup time by the Bourne, BASH , or C shells.
 These allow the system administrator to set global defaults for all users. 
 Users can also create individual copies of these in their home directory to personalize their environment.

> /etc/shells
>> ists trusted shells. The chsh command allows users to change their login shell only to shells listed in this file. 
ftpd, is the server process that provides FTP services for a machine, will check that the user's shell is listed in /etc/shells and will not let people log in unless the shell is listed there.

```

### 6) /home : Users’ home directories, containing saved files, personal settings, etc

### 7) /lib : Libraries essential for the binaries in /bin/ and /sbin/

```text
Shared libraries needed by the programs on the root filesystem.

The /lib directory contains kernel modules and those shared library images (the C programming code library) needed to boot the system and run the commands in the root filesystem, ie. by binaries in /bin and /sbin

> /lib/security
>> PAM library files.

> /lib/modules/'kernel-version'
>> The home of all the kernel modules.

> /lib/'machine-architecture'
>> Contains platform/architecture dependent libraries

> /lib/iptables
>> iptables shared library files.

Library filenames are either ld* or lib*.so.*
Example: ld-2.11.1.so, libncurses.so.5.7
```

### 8) /media : Mount points for removable media such as CD-ROMs (appeared in FHS-2.3)

```text
Temporary mount directory for removable devices.
Examples, /media/cdrom for CD-ROM; /media/floppy for floppy drives; /media/cdrecorder for CD writer
```

### 9) /mnt : Temporarily mounted filesystems.

```text
Temporary mount directory where sysadmins can mount filesystems
```

### 10) /opt : Optional application software packages

```text
Contains add-on applications from individual vendors.
Add-on applications should be installed under either /opt/ or /opt/ sub-directory
```

### 11) /sbin : Essential system binaries, e.g., fsck, init, route

```text
Just like /bin, /sbin also contains binary executables.
/sbin should contain only binaries essential for booting, restoring,recovering, and/or repairing the system in addition to the binaries in /bin.

The linux commands located under this directory are used typically by system administrator, for system maintenance purpose.
Example: iptables, reboot, fdisk, ifconfig, swapon
```

### 12) /srv : Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems

```text
srv stands for service.
Contains server specific services related data.
Example, /srv/cvs contains CVS related data.
```

### 13) /tmp : Temporary files. Often not preserved between system reboots, and may be severely size restricted

```text
Directory that contains temporary files created by system and users.
Files under this directory are deleted when system is rebooted.
```

### 14) /usr : Secondary hierarchy for read-only user data; contains the majority of (multi-)user utilities and applications

```text
Contains binaries, libraries, documentation, and source-code for second level programs.

Files in /usr usually come from a Linux distribution;

> /usr/bin 
>> contains binary files for user programs. If you can’t find a user binary under /bin, look under /usr/bin. For example: awk, cc, less, scp

> /usr/sbin 
>> contains binary files for system administrators. If you can’t find a system binary under /sbin, look under /usr/sbin. For example: atd, cron, sshd, useradd, userdel

> /usr/share/man, /usr/share/info, /usr/share/doc
>> Manual pages, GNU Info documents, and miscellaneous other documentation files, respectively.

> /usr/lib 
>> contains libraries for /usr/bin and /usr/sbin

> /usr/local 
>> contains users programs that you install from source. For example, when you install apache from source, it goes under /
usr/local/apache2

> /usr/src 
>> holds the Linux kernel sources, header-files and documentation.

```

### 15) /proc : Virtual filesystem providing process and kernel information as files. In Linux, corresponds to a procfs mount. Generally automatically generated and populated by the system, on the fly

```text
Contains information about system process.
The /proc filesystem contains a illusionary filesystem.
It does not exist on a disk. Instead, the kernel creates it in memory.
It is used to provide information about the system
This is a pseudo filesystem contains information about running process. For example: /proc/{pid} directory contains information about the process with that particular pid.

> /proc/ioports
>> Which I/O ports are in use at the moment.

> /proc/cpuinfo
>> Information about the processor, such as its type, make, model, and performance.

> /proc/interrupts
>> Shows which interrupts are in use, and how many of each there have been.

> /proc/kmsg
>> Messages output by the kernel. These are also routed to syslog.

> /proc/net
>> Status information about network protocols.

> /proc/stat
>> Various statistics about the system, such as the number of page faults since the system was booted.

> /proc/uptime
>> The time the system has been up.

> /proc/version
>> The kernel version.

> /proc/loadavg
>> The `load average' of the system; three meaningless indicators of how much work the system has to do at the moment.

> /proc/meminfo
>> Information about memory usage, both physical and swap.

> /proc/devices
>> List of device drivers configured into the currently running kernel.
This is a virtual filesystem with text information about system resources. For example: /proc/uptime
```

### 16) /var : Contains data that is changed when the system is running normally

```text
> /var/log
>> Log files from various programs, especially login(/var/log/wtmp, which logs all logins and logouts into the system)
syslog(/var/log/messages, where all kernel and system program message are usually stored). 
Files in /var/log can often grow indefinitely, and may require cleaning at regular intervals.

> /var/mail
>> This is the FHS approved location for user mailbox files

> /var/run
>> Files that contain information about the system that is valid until the system is next booted.
 For example, /var/run/utmp contains information about people currently logged in.

> /var/spool
>> Directories for news, printer queues, and other queued work

> /var/local
>> Variable data for programs that are installed in /usr/local

> /var/lock
>> Lock files. Many programs follow a convention to create a lock file in /var/lock to indicate that they are using a particular device or file. 
Other programs will notice the lock file and won't attempt to use the device or file.
```
