HDFS Lab: Replicate to another cluster:
========================================
Create partners directory and generate 500Mb terragen file:
============================================================

500 MB file = 1024 (KB) x 1024 (MB) x 500 (500 MB) / 100 (Byte) = 5242880
==========================================================================


[root@ip-172-31-36-240 ~]# sudo su hdfs
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -mkdir /willwatters
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /
Found 3 items
drwxrwxrwt   - hdfs supergroup          0 2018-10-16 23:14 /tmp
drwxr-xr-x   - hdfs supergroup          0 2018-10-16 23:14 /user
drwxr-xr-x   - hdfs supergroup          0 2018-10-17 01:00 /willwatters
[hdfs@ip-172-31-36-240 root]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen 5242880 /ronniet7626
18/10/17 01:01:41 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-47-204.eu-west-3.compute.internal/172.31.47.204:8032
18/10/17 01:01:42 INFO terasort.TeraGen: Generating 5242880 using 2
18/10/17 01:01:42 INFO mapreduce.JobSubmitter: number of splits:2
18/10/17 01:01:42 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539731832847_0001
18/10/17 01:01:42 INFO impl.YarnClientImpl: Submitted application application_1539731832847_0001
18/10/17 01:01:42 INFO mapreduce.Job: The url to track the job: http://ip-172-31-47-204.eu-west-3.compute.internal:8088/proxy/application_1539731832847_0001/
18/10/17 01:01:42 INFO mapreduce.Job: Running job: job_1539731832847_0001
18/10/17 01:01:49 INFO mapreduce.Job: Job job_1539731832847_0001 running in uber mode : false
18/10/17 01:01:49 INFO mapreduce.Job:  map 0% reduce 0%
18/10/17 01:02:00 INFO mapreduce.Job:  map 100% reduce 0%
18/10/17 01:02:00 INFO mapreduce.Job: Job job_1539731832847_0001 completed successfully
18/10/17 01:02:00 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=296158
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=167
		HDFS: Number of bytes written=524288000
		HDFS: Number of read operations=8
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=4
	Job Counters
		Launched map tasks=2
		Other local map tasks=2
		Total time spent by all maps in occupied slots (ms)=14851
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=14851
		Total vcore-milliseconds taken by all map tasks=14851
		Total megabyte-milliseconds taken by all map tasks=15207424
	Map-Reduce Framework
		Map input records=5242880
		Map output records=5242880
		Input split bytes=167
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=265
		CPU time spent (ms)=10450
		Physical memory (bytes) snapshot=732811264
		Virtual memory (bytes) snapshot=3157049344
		Total committed heap usage (bytes)=874512384
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=11257830824958050
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=524288000

Replicate to partners Cluster using distcp
==========================================

Unable to connect to partners cluster due to security lock down in AWS
=======================================================================

Instead using distcp tp copy  data within my own cluster
==========================================================


[hdfs@ip-172-31-36-240 root]$ hadoop distcp /ronniet7626 /user/ronniet_dist_copy
18/10/17 01:03:56 INFO tools.OptionsParser: parseChunkSize: blocksperchunk false
18/10/17 01:03:57 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[/ronniet7626], targetPath=/user/ronniet_dist_copy, targetPathExists=false, filtersFile='null', blocksPerChunk=0, copyBufferSize=8192}
18/10/17 01:03:57 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-47-204.eu-west-3.compute.internal/172.31.47.204:8032
18/10/17 01:03:58 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 4; dirCnt = 1
18/10/17 01:03:58 INFO tools.SimpleCopyListing: Build file listing completed.
18/10/17 01:03:58 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
18/10/17 01:03:58 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
18/10/17 01:03:58 INFO tools.DistCp: Number of paths in the copy list: 4
18/10/17 01:03:58 INFO tools.DistCp: Number of paths in the copy list: 4
18/10/17 01:03:58 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-47-204.eu-west-3.compute.internal/172.31.47.204:8032
18/10/17 01:03:58 INFO mapreduce.JobSubmitter: number of splits:3
18/10/17 01:03:58 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539731832847_0002
18/10/17 01:03:58 INFO impl.YarnClientImpl: Submitted application application_1539731832847_0002
18/10/17 01:03:58 INFO mapreduce.Job: The url to track the job: http://ip-172-31-47-204.eu-west-3.compute.internal:8088/proxy/application_1539731832847_0002/
18/10/17 01:03:58 INFO tools.DistCp: DistCp job-id: job_1539731832847_0002
18/10/17 01:03:58 INFO mapreduce.Job: Running job: job_1539731832847_0002
18/10/17 01:04:04 INFO mapreduce.Job: Job job_1539731832847_0002 running in uber mode : false
18/10/17 01:04:04 INFO mapreduce.Job:  map 0% reduce 0%
18/10/17 01:04:11 INFO mapreduce.Job:  map 33% reduce 0%
18/10/17 01:04:13 INFO mapreduce.Job:  map 100% reduce 0%
18/10/17 01:04:14 INFO mapreduce.Job: Job job_1539731832847_0002 completed successfully
18/10/17 01:04:14 INFO mapreduce.Job: Counters: 33
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=455019
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=524289816
		HDFS: Number of bytes written=524288000
		HDFS: Number of read operations=50
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=13
	Job Counters
		Launched map tasks=3
		Other local map tasks=3
		Total time spent by all maps in occupied slots (ms)=16446
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=16446
		Total vcore-milliseconds taken by all map tasks=16446
		Total megabyte-milliseconds taken by all map tasks=16840704
	Map-Reduce Framework
		Map input records=4
		Map output records=0
		Input split bytes=342
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=235
		CPU time spent (ms)=6500
		Physical memory (bytes) snapshot=717713408
		Virtual memory (bytes) snapshot=4756672512
		Total committed heap usage (bytes)=1113063424
	File Input Format Counters
		Bytes Read=1474
	File Output Format Counters
		Bytes Written=0
	DistCp Counters
		Bytes Copied=524288000
		Bytes Expected=524288000
		Files Copied=4

Verifying the copy
===================

[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user/
Found 3 items
drwx------   - hdfs   supergroup          0 2018-10-17 01:01 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2018-10-16 23:14 /user/history
drwxr-xr-x   - hdfs   supergroup          0 2018-10-17 01:04 /user/ronniet_dist_copy
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user/ronniet_dist_copy
Found 3 items
-rw-r--r--   3 hdfs supergroup          0 2018-10-17 01:04 /user/ronniet_dist_copy/_SUCCESS
-rw-r--r--   3 hdfs supergroup  262144000 2018-10-17 01:04 /user/ronniet_dist_copy/part-m-00000
-rw-r--r--   3 hdfs supergroup  262144000 2018-10-17 01:04 /user/ronniet_dist_copy/part-m-00001

Browse the results
Use hdfs fsck <path> -files -blocks on your source and target directories
==========================================================================

Source file
============

hdfs@ip-172-31-36-240 root]$ hdfs fsck /ronniet7626 -files -blocks
Connecting to namenode via http://ip-172-31-36-240.eu-west-3.compute.internal:50070/fsck?ugi=hdfs&files=1&blocks=1&path=%2Fronniet7626
FSCK started by hdfs (auth:SIMPLE) from /172.31.36.240 for path /ronniet7626 at Wed Oct 17 01:15:58 UTC 2018
/ronniet7626 <dir>
/ronniet7626/_SUCCESS 0 bytes, 0 block(s):  OK

/ronniet7626/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-1279653333-172.31.36.240-1539731605427:blk_1073741934_1110 len=134217728 Live_repl=3
1. BP-1279653333-172.31.36.240-1539731605427:blk_1073741938_1114 len=127926272 Live_repl=3

/ronniet7626/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-1279653333-172.31.36.240-1539731605427:blk_1073741935_1111 len=134217728 Live_repl=3
1. BP-1279653333-172.31.36.240-1539731605427:blk_1073741937_1113 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Wed Oct 17 01:15:58 UTC 2018 in 1 milliseconds


The filesystem under path '/ronniet7626' is HEALTHY
[hdfs@ip-172-31-36-240 root]$

Destination file
=================

[hdfs@ip-172-31-36-240 root]$ hdfs fsck /user/ronniet_dist_copy -files -blocks
Connecting to namenode via http://ip-172-31-36-240.eu-west-3.compute.internal:50070/fsck?ugi=hdfs&files=1&blocks=1&path=%2Fuser%2Fronniet_dist_copy
FSCK started by hdfs (auth:SIMPLE) from /172.31.36.240 for path /user/ronniet_dist_copy at Wed Oct 17 01:06:47 UTC 2018
/user/ronniet_dist_copy <dir>
/user/ronniet_dist_copy/_SUCCESS 0 bytes, 0 block(s):  OK

/user/ronniet_dist_copy/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-1279653333-172.31.36.240-1539731605427:blk_1073741957_1133 len=134217728 Live_repl=3
1. BP-1279653333-172.31.36.240-1539731605427:blk_1073741960_1136 len=127926272 Live_repl=3

/user/ronniet_dist_copy/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-1279653333-172.31.36.240-1539731605427:blk_1073741956_1132 len=134217728 Live_repl=3
1. BP-1279653333-172.31.36.240-1539731605427:blk_1073741959_1135 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Wed Oct 17 01:06:47 UTC 2018 in 3 milliseconds


The filesystem under path '/user/ronniet_dist_copy' is HEALTHY
[hdfs@ip-172-31-36-240 root]$ 