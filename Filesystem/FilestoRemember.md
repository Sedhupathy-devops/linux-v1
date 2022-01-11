# Important files and it's use cases

## /dev/null

### use case 1 (Redirecting stderr to /dev/null)

```bash
grep -r hello /sys/ 2> /dev/null  #redirect error output to dev/null
```

### use case 2 (Redirecting stdout to /dev/null)

```bash
 ping google.com 1> /dev/null #it will only output error messeges
```

### use case 3 (Redirect all output to /dev/null)

```bash
 grep -r hello /sys/ > /dev/null 2>&1 #both error and success report won't be displayed
 grep -r hello /sys/ &> /dev/null   #both error and success report won't be displayed
```

## /etc/passwd

### use case 1(to get users list)

```bash
cut -d: -f1 /etc/passwd #list usernames only
cut -d : -f 1,6 /etc/passwd #list username with it's homedir
```
### use case 2(to get a user info)

``` bash
grep user1 /etc/passwd #displays username userid groupid homedir and shell
```

## /etc/shadow (passwords stored)

```bash
tail /etc/shadow
```

## /etc/group (groups info)

```bash
tail /etc/group
```

## proc/cpuinfo (to get cpu info)

```bash
cat /proc/cpuinfo
```

## /proc/uptime (To get system uptime)

```bash
cat /proc/uptime
```

## /proc/version (To get kernel version)

```bash
cat /proc/version
```

## /proc/meminfo (To get memory info)

```bash
cat /proc/meminfo
```

## /var/log (To watch logs)

```bash
sudo tail -f /var/log/syslog #to get system logs
```

## /var/mail (To get mail infos)

```bash

```

## /var/run/utmp (contains info on users currently logged in)

```bash

```

## /usr/share/man (man pages are stored)

## /etc/profile(Linux system wide environment and startup programs)

## /etc/shells(list of shells available)
