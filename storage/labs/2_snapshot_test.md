HDFS Lab: Test HDFS Snapshots
=============================

Create a precious directory in HDFS; copy the ZIP course file into it.

[hdfs@ip-172-31-36-240 root]$ hdfs dfs -mkdir /precious
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /
Found 5 items
drwxr-xr-x   - hdfs supergroup          0 2018-10-17 01:58 /precious
drwxr-xr-x   - hdfs supergroup          0 2018-10-17 01:01 /ronniet7626
drwxrwxrwt   - hdfs supergroup          0 2018-10-16 23:14 /tmp
drwxr-xr-x   - hdfs supergroup          0 2018-10-17 01:31 /user
drwxr-xr-x   - hdfs supergroup          0 2018-10-17 01:00 /willwatters

Copy the zip file from local laptop to native file system on ec2 datanode:

➜  labs git:(master) scp -i /Users/ronniet/bootcamp_keys.pem /Users/ronniet/Desktop/SEBC-master.zip centos@ec2-52-47-152-180.eu-west-3.compute.amazonaws.com:/tmp
SEBC-master.zip

Copy the zip file into the precious directory:
=================================================

[hdfs@ip-172-31-36-240 root]$ cd /tmp
[hdfs@ip-172-31-36-240 tmp]$ hdfs dfs -put SEBC-master.zip /precious
[hdfs@ip-172-31-36-240 tmp]$ hdfs dfs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup    1720611 2018-10-17 02:07 /precious/SEBC-master.zip

Enable snapshots for precious:
==============================

Enable the snapshot from the Cluster GUI, HDFS>File Browser > select precious > select top right arrow and click Enable Snapshot

Create a snapshot called sebc-hdfs-test
========================================

Browse to HDFS>File Browser > precious click take snapshot, call snapshot sebc-hdfs-test

Delete the directory:
======================

Failed to delete directory as is snapshotable:

hdfs dfs -rm -r /precious
rm: Failed to move to trash: hdfs://ip-172-31-36-240.eu-west-3.compute.internal:8020/precious: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
[hdfs@ip-172-31-36-240 tmp]$

Delete the ZIP file:
====================

[hdfs@ip-172-31-36-240 tmp]$ hdfs dfs -rm -r /precious/SEBC-master.zip
18/10/17 02:19:50 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-36-240.eu-west-3.compute.internal:8020/precious/SEBC-master.zip' to trash at: hdfs://ip-172-31-36-240.eu-west-3.compute.internal:8020/user/hdfs/.Trash/Current/precious/SEBC-master.zip

[hdfs@ip-172-31-36-240 tmp]$ hdfs dfs -ls /precious
[hdfs@ip-172-31-36-240 tmp]$

Restore the deleted file:
=========================

HDFS > File Browser > select precious
select top right arrow and click "Restore Directory From Snapshot"
select the "sebc-hdfs-test" snapshot
select "HDFS copy" option for the restore
click "restore"
