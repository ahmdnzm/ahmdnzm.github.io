---
title: sudo still asking password although set NOPASSWD in visudo
date: 2023-05-24 12:00:00 +0800
categories: [Linux]
tags: [linux, bash, sudo]     # TAG names should always be lowercase
image:
  path: /assets/img/cli.jpg
---
# sudo still asking password although set NOPASSWD in visudo

## Challenge

```shell
pi@ubuntu:~$ sudo apt update && sudo apt upgrade -y
[sudo] password for pi:
```

## Solution

Run visudo

```shell
sudo visudo
```

```shell
 43 # User privilege specification
 44 root    ALL=(ALL:ALL) ALL
 45 pi      ALL=(ALL:ALL) NOPASSWD: ALL
 46
 47 # Members of the admin group may gain root privileges
 48 %admin ALL=(ALL) ALL
 49
 50 # Allow members of group sudo to execute any command
 51 %sudo   ALL=(ALL:ALL) ALL
 52
 53 # See sudoers(5) for more information on "@include" directives:
 54
 55 @includedir /etc/sudoers.d
```

Delete particular user privilege settings in visudo. For this example, on line 45

```shell
 45 pi      ALL=(ALL:ALL) NOPASSWD: ALL
```

create a new file in /etc/sudoers.d

```shell
sudo vim /etc/sudoers.d/users
```

Insert the user privilege settings inside the file

```shell
# User privilege specification
pi      ALL=(ALL:ALL) NOPASSWD: ALL
```

Run sudo again to confirm sudo doesn’t ask for password