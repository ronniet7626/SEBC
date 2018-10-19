The hostname of your DB node
=============================

ip-172-31-38-93.eu-west-3.compute.internal

The command screenshot to display the DB version
=================================================

root@ip-172-31-38-93 mysql-connector-java-5.1.47]# mysql --version
mysql  Ver 15.1 Distrib 5.5.60-MariaDB, for Linux (x86_64) using readline 5.1


The command and output for listing databases
=============================================

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)

MariaDB [(none)]>