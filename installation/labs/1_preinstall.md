1. Check vm.swappiness on all your nodes
Set the value to 1 if necessary
Command used 

echo 1 > /proc/sys/vm/swappiness

#cat /proc/sys/vm/swappiness
1

2. Show the mount attributes of all volumes

[root@ip-172-31-41-139 etc]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p1   30G  973M   30G   4% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           7.6G   17M  7.6G   1% /run
tmpfs           7.6G     0  7.6G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000
tmpfs           1.6G     0  1.6G   0% /run/user/0
[root@ip-172-31-41-139 etc]# cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Tue Jun  5 14:06:12 2018
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=8c1540fa-e2b4-407d-bcd1-59848a73e463 /                       xfs     defaults,noatime        0 0

3.	Show the reserve space of any non-root, ext-based volumes
XFS volumes do not maintain reserve space

Using xfs filesystem no reserve space is maintained.

4.	Disable transparent hugepage support

echo never > /sys/kernel/mm/transparent_hugepage/enabled

echo never > /sys/kernel/mm/transparent_hugepage/defrag

To make persistant:

chmod +x /etc/rc.d/rc.local

echo "echo never > /sys/kernel/mm/transparent_hugepage/enabled" >> /etc/rc.local

echo "echo never > /sys/kernel/mm/transparent_hugepage/defrag" >> /etc/rc.local

5.	List your network interface configuration

[root@ip-172-31-41-139 network-scripts]# cat ifcfg-ens5
# Created by cloud-init on instance boot automatically, do not edit.
#
BOOTPROTO=dhcp
DEVICE=ens5
HWADDR=0e:01:80:01:75:4c
ONBOOT=yes
TYPE=Ethernet
USERCTL=no
[root@ip-172-31-41-139 network-scripts]# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP group default qlen 1000
    link/ether 0e:01:80:01:75:4c brd ff:ff:ff:ff:ff:ff
    inet 172.31.41.139/20 brd 172.31.47.255 scope global dynamic ens5
       valid_lft 2907sec preferred_lft 2907sec
    inet6 fe80::c01:80ff:fe01:754c/64 scope link
       valid_lft forever preferred_lft forever
[root@ip-172-31-41-139 network-scripts]#

6.	List forward and reverse host lookups using getent or nslookup

[root@ip-172-31-41-139 network-scripts]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.41.139   ip-172-31-41-139.eu-west-3.compute.internal cm
172.31.38.248   ip-172-31-38-248.eu-west-3.compute.internal node1
172.31.38.36    ip-172-31-38-36.eu-west-3.compute.internal node2
172.31.36.222   ip-172-31-36-222.eu-west-3.compute.internal node3
172.31.37.221   ip-172-31-37-221.eu-west-3.compute.internal node4

7.	Show the nscd service is running

[root@ip-172-31-41-139 network-scripts]# systemctl status nscd
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 13:38:17 UTC; 13min ago
  Process: 524 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 527 (nscd)
   CGroup: /system.slice/nscd.service
           └─527 /usr/sbin/nscd

Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitoring file `/etc/services` (6)
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitoring directory `/etc` (2)
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 disabled inotify-based monitoring for file `/etc/netgroup':...tory
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 stat failed for file `/etc/netgroup'; will try again later:...tory
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal systemd[1]: Started Name Service Cache Daemon.
Oct 15 13:38:18 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitored file `/etc/resolv.conf` was written to
Oct 15 13:38:20 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitored file `/etc/resolv.conf` was written to
Oct 15 13:38:20 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitoring file `/etc/resolv.conf` (5)
Oct 15 13:38:20 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 monitoring directory `/etc` (2)
Oct 15 13:38:37 ip-172-31-41-139.eu-west-3.compute.internal nscd[527]: 527 checking for monitored file `/etc/netgroup': No such file o...tory
Hint: Some lines were ellipsized, use -l to show in full.


8.	Show the ntpd service is running

[root@ip-172-31-41-139 network-scripts]# systemctl status ntpd
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2018-10-15 13:38:17 UTC; 14min ago
  Process: 521 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 544 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─544 /usr/sbin/ntpd -u ntp:ntp -g

Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c016 06 restart
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c011 01 freq_not_set
Oct 15 13:38:17 ip-172-31-41-139.eu-west-3.compute.internal systemd[1]: Started Network Time Service.
Oct 15 13:38:22 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: Listen normally on 4 ens5 172.31.41.139 UDP 123
Oct 15 13:38:22 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: Listen normally on 5 ens5 fe80::c01:80ff:fe01:754c UDP 123
Oct 15 13:38:22 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: new interface(s) found: waking up resolver
Oct 15 13:38:29 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c61c 0c clock_step +0.951379 s
Oct 15 13:38:30 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c614 04 freq_mode
Oct 15 13:38:31 ip-172-31-41-139.eu-west-3.compute.internal ntpd[544]: 0.0.0.0 c618 08 no_sys_peer


Also disabled chrony.d to remove any possible conflicts:

root@ip-172-31-41-139 network-scripts]# systemctl status chronyd
● chronyd.service - NTP client/server
   Loaded: loaded (/usr/lib/systemd/system/chronyd.service; disabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:chronyd(8)
           man:chrony.conf(5)


