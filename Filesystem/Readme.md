# Filesystem

## list

### / (Root): Primary hierarchy root and root directory of the entire file system hierarchy. 

```text
Every single file and directory starts from the root directory
The only root user has the right to write under this directory
/root is the root user’s home directory, which is not the same as /
```

### /bin : Essential command binaries that need to be available in single-user mode; for all users, e.g., cat, ls, cp

```text
Contains binary executables
Common linux commands you need to use in single-user modes are located under this directory.
Commands used by all the users of the system are located here e.g. ps, ls, ping, grep, cp
```

### /boot : Boot loader files, e.g., kernels, initrd 

```text
Kernel initrd, vmlinux, grub files are located under /boot
Example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic
```

### /dev : Essential device files, e.g., /dev/null

```text
These include terminal devices, usb, or any device attached to the system.
Example: /dev/tty1, /dev/usbmon0
```

### /etc : Host-specific system-wide configuration files

```text
Contains configuration files required by all programs.
This also contains startup and shutdown shell scripts used to start/stop individual programs.
Example: /etc/resolv.conf, /etc/logrotate.conf.
```

### /home : Users’ home directories, containing saved files, personal settings, etc

### /lib : Libraries essential for the binaries in /bin/ and /sbin/.

```text
Library filenames are either ld* or lib*.so.*
Example: ld-2.11.1.so, libncurses.so.5.7
```

### /media : Mount points for removable media such as CD-ROMs (appeared in FHS-2.3)

```text
Temporary mount directory for removable devices.
Examples, /media/cdrom for CD-ROM; /media/floppy for floppy drives; /media/cdrecorder for CD writer
```

### /mnt : Temporarily mounted filesystems.

```text
Temporary mount directory where sysadmins can mount filesystems
```

### opt : Optional application software packages

```text
Contains add-on applications from individual vendors.
Add-on applications should be installed under either /opt/ or /opt/ sub-directory
```

### /sbin : Essential system binaries, e.g., fsck, init, route

```text
ust like /bin, /sbin also contains binary executables.
The linux commands located under this directory are used typically by system administrator, for system maintenance purpose.
Example: iptables, reboot, fdisk, ifconfig, swapon
```

### /srv : Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems

```text
srv stands for service.
Contains server specific services related data.
Example, /srv/cvs contains CVS related data.
```

### /tmp : Temporary files. Often not preserved between system reboots, and may be severely size restricted

```text
Directory that contains temporary files created by system and users.
Files under this directory are deleted when system is rebooted.
```

### /usr : Secondary hierarchy for read-only user data; contains the majority of (multi-)user utilities and applications

```text
Contains binaries, libraries, documentation, and source-code for second level programs.
/usr/bin contains binary files for user programs. If you can’t find a user binary under /bin, look under /usr/bin. For example: at, awk, cc, less, scp
/usr/sbin contains binary files for system administrators. If you can’t find a system binary under /sbin, look under /usr/sbin. For example: atd, cron, sshd, useradd, userdel
/usr/lib contains libraries for /usr/bin and /usr/sbin
/usr/local contains users programs that you install from source. For example, when you install apache from source, it goes under /usr/local/apache2
/usr/src holds the Linux kernel sources, header-files and documentation.
```

### proc : Virtual filesystem providing process and kernel information as files. In Linux, corresponds to a procfs mount. Generally automatically generated and populated by the system, on the fly

```text
Contains information about system process.
This is a pseudo filesystem contains information about running process. For example: /proc/{pid} directory contains information about the process with that particular pid.
This is a virtual filesystem with text information about system resources. For example: /proc/uptime
```
