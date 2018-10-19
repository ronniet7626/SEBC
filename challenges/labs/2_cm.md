List the command and output of ls /etc/yum.repos.d
====================================================

[root@ip-172-31-37-49 yum.repos.d]# ls -l
total 36
-rw-r--r--. 1 root root 1664 May 17 13:53 CentOS-Base.repo
-rw-r--r--. 1 root root 1309 May 17 13:53 CentOS-CR.repo
-rw-r--r--. 1 root root  649 May 17 13:53 CentOS-Debuginfo.repo
-rw-r--r--. 1 root root  314 May 17 13:53 CentOS-fasttrack.repo
-rw-r--r--. 1 root root  630 May 17 13:53 CentOS-Media.repo
-rw-r--r--. 1 root root 1331 May 17 13:53 CentOS-Sources.repo
-rw-r--r--. 1 root root 4768 May 17 13:53 CentOS-Vault.repo
-rw-r--r--. 1 root root  294 Oct 19 08:11 cloudera-manager.repo

Use the scm_prepare_database.sh script to write your db.properties file
List the full command line in 2_cm.md
==============================================================

/usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-172-31-38-93.eu-west-3.compute.internal -utemp -ptraining --scm-host ip-172-31-37-49.eu-west-3.compute.internal   scm scm training --force

[root@ip-172-31-37-49 cloudera-scm-server]# ll
total 8
-rw-------. 1 cloudera-scm cloudera-scm  462 Oct 19 08:58 db.properties
-rw-r--r--. 1 root         root         2229 Jul  7 05:20 log4j.properties

