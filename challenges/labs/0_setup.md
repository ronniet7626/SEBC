List the cloud provider you are using
======================================

AWS

List the Linux release you have chosen
=======================================

[root@ip-172-31-37-49 ~]# cat /etc/redhat-release
CentOS Linux release 7.5.1804 (Core)


Show that the disk space on each node is at least 30 GB
========================================================

[root@ip-172-31-37-49 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  2.0G   29G   7% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000

[root@ip-172-31-38-93 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  2.2G   28G   8% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000

[root@ip-172-31-41-159 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  975M   30G   4% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000

[root@ip-172-31-34-168 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  975M   30G   4% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000

[root@ip-172-31-47-234 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  975M   30G   4% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000

List the command and output for yum repolist enabled
=====================================================
root@ip-172-31-37-49 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.quelquesmots.fr
 * extras: centos.crazyfrogs.org
 * updates: centos.crazyfrogs.org
repo id                                                                                         repo name                                                                                         status
base/7/x86_64                                                                                   CentOS-7 - Base                                                                                   9,911
extras/7/x86_64                                                                                 CentOS-7 - Extras                                                                                   432
updates/7/x86_64                                                                                CentOS-7 - Updates                                                                                1,561
repolist: 11,904

==========================================================================================================
[root@ip-172-31-38-93 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.quelquesmots.fr
 * extras: centos.crazyfrogs.org
 * updates: centos.crazyfrogs.org
repo id                                                                                         repo name                                                                                         status
!base/7/x86_64                                                                                  CentOS-7 - Base                                                                                   9,911
!extras/7/x86_64                                                                                CentOS-7 - Extras                                                                                   432
!updates/7/x86_64                                                                               CentOS-7 - Updates                                                                                1,561
repolist: 11,904
=============================================================================================================
[root@ip-172-31-41-159 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.mirror.fr.planethoster.net
 * extras: centos.crazyfrogs.org
 * updates: centos.mirror.fr.planethoster.net
repo id                                                                                         repo name                                                                                         status
!base/7/x86_64                                                                                  CentOS-7 - Base                                                                                   9,911
!extras/7/x86_64                                                                                CentOS-7 - Extras                                                                                   432
!updates/7/x86_64                                                                               CentOS-7 - Updates                                                                                1,561
repolist: 11,904
=============================================================================================================

[root@ip-172-31-34-168 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.mirror.fr.planethoster.net
 * extras: centos.crazyfrogs.org
 * updates: centos.mirror.fr.planethoster.net
repo id                                                                                         repo name                                                                                         status
!base/7/x86_64                                                                                  CentOS-7 - Base                                                                                   9,911
!extras/7/x86_64                                                                                CentOS-7 - Extras                                                                                   432
!updates/7/x86_64                                                                               CentOS-7 - Updates                                                                                1,561
repolist: 11,904
=============================================================================================================

[root@ip-172-31-47-234 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.mirror.fr.planethoster.net
 * extras: centos.crazyfrogs.org
 * updates: centos.crazyfrogs.org
repo id                                                                                         repo name                                                                                         status
!base/7/x86_64                                                                                  CentOS-7 - Base                                                                                   9,911
!extras/7/x86_64                                                                                CentOS-7 - Extras                                                                                   432
!updates/7/x86_64                                                                               CentOS-7 - Updates                                                                                1,561
repolist: 11,904

Create local users and groups:
==============================
[root@ip-172-31-37-49 ~]# cat /etc/passwd
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
[root@ip-172-31-37-49 ~]# cat /etc/group
hotels:x:1001:fullerton
shops:x:1002:raffles
[root@ip-172-31-37-49 ~]#
=============================================================================================================

[root@ip-172-31-38-93 ~]# cat /etc/passwd
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
[root@ip-172-31-38-93 ~]#


[root@ip-172-31-38-93 ~]# cat /etc/group
hotels:x:3001:fullerton
shops:x:3002:raffles
[root@ip-172-31-38-93 ~]#
=============================================================================================================

[root@ip-172-31-41-159 ~]# cat /etc/passwd
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
[root@ip-172-31-41-159 ~]#

[root@ip-172-31-41-159 ~]# cat /etc/group
hotels:x:1001:fullerton
shops:x:1002:raffles
[root@ip-172-31-41-159 ~]#

=============================================================================================================

[root@ip-172-31-34-168 ~]# cat /etc/passwd
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
[root@ip-172-31-34-168 ~]#

[root@ip-172-31-34-168 ~]# cat /etc/group
hotels:x:1001:fullerton
shops:x:1002:raffles
[root@ip-172-31-34-168 ~]#

=============================================================================================================

[root@ip-172-31-47-234 ~]# cat /etc/passwd
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
[root@ip-172-31-47-234 ~]#

[root@ip-172-31-47-234 ~]# cat /etc/group
hotels:x:1001:fullerton
shops:x:1002:raffles
[root@ip-172-31-47-234 ~]#

