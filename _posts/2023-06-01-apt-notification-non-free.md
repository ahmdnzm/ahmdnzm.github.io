---
title: apt-key non-free split notification
date: 2023-06-01 12:00:00 +0800
categories: [Linux]
tags: [linux, debian, bash, apt]     # TAG names should always be lowercase
# image:
#   path: /assets/img/cli.jpg
---
# apt notification about changed its 'non-free component' value from 'non-free' to 'non-free non-free-firmware'

After upgrading to Debian 12, I started having the following apt notifcation after running an apt update command


```shell
sudo apt update
```

Output

```shell
N: Repository 'Debian bookworm' changed its 'non-free component' value from 'non-free' to 'non-free non-free-firmware'
N: More information about this can be found online in the Release notes at: https://www.debian.org/releases/bookworm/arm64/release-notes/ch-information.html#non-free-split
```

Solution

Check `sources.list` for non-free option

```shell
grep non-free /etc/apt/sources.list
```

Output

```shell
deb http://deb.debian.org/debian bookworm main contrib non-free
deb http://security.debian.org/debian-security bookworm-security main contrib non-free
deb http://deb.debian.org/debian bookworm-updates main contrib non-free
#deb-src http://deb.debian.org/debian bookworm main contrib non-free
#deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free
#deb-src http://deb.debian.org/debian bookworm-updates main contrib non-free
```

Add `non-free-firmware` in the sources.list

```shell
sudo sed -i "s/non-free/non-free non-free-firmware/g" /etc/apt/sources.list
```

Check again the sources.list to confirm `non-free-firmware` added into the file.

```shell
grep non-free /etc/apt/sources.list
```

Output


```shell
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
#deb-src http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
#deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
#deb-src http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
```

Do `sudo apt update` again to confirm that apt changed notification is gone