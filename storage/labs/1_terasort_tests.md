HDFS Lab: Test HDFS performance
===============================

Create an end-user Linux account named with your GitHub handle
Create a home HDFS directory for this user as well
===================================================

New user with github handle as name created on all nodes:

[root@ip-172-31-44-13 ~]# useradd ronniet7626
[root@ip-172-31-44-13 ~]# passwd ronniet7626
Changing password for user ronniet7626

Create home HDFS Directory:
============================

[root@ip-172-31-36-240 ~]# sudo su hdfs
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -mkdir /user/ronniet7626
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user
Found 4 items
drwx------   - hdfs   supergroup          0 2018-10-17 01:01 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2018-10-16 23:14 /user/history
drwxr-xr-x   - hdfs   supergroup          0 2018-10-17 01:31 /user/ronniet7626
drwxr-xr-x   - hdfs   supergroup          0 2018-10-17 01:04 /user/ronniet_dist_copy
[hdfs@ip-172-31-36-240 root]$

Change Ownership of new users hdfs home directory:

[hdfs@ip-172-31-36-240 root]$ hdfs dfs -chown -R ronniet7626:ronniet7626 /user/ronniet7626
[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user
Found 4 items
drwx------   - hdfs        supergroup           0 2018-10-17 01:01 /user/hdfs
drwxrwxrwx   - mapred      hadoop               0 2018-10-16 23:14 /user/history
drwxr-xr-x   - ronniet7626 ronniet7626          0 2018-10-17 01:31 /user/ronniet7626
drwxr-xr-x   - hdfs        supergroup           0 2018-10-17 01:04 /user/ronniet_dist_copy

Create a 10 GB file using teragen
==================================

(1024 (KB) x 1024 (MB) x 1024 (GB) x 10 (10 GB) / 100 (Byte) = 107374182)

Set the number of mappers to four
==================================

Limit the block size to 32 MB
==============================
(1024 (KB) x 1024 (MB) x 32 (MB) = 33554432 (Bytes))

Land the result under your user's home directory
=================================================
Use the time command to report the job's duration
===================================================

[hdfs@ip-172-31-36-240 root]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapreduce.job.maps=4 -Ddfs.blocksize=33554432 107374182 /user/ronniet7626/teragen
18/10/17 01:39:29 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-47-204.eu-west-3.compute.internal/172.31.47.204:8032
18/10/17 01:39:30 INFO terasort.TeraGen: Generating 107374182 using 4
18/10/17 01:39:30 INFO mapreduce.JobSubmitter: number of splits:4
18/10/17 01:39:30 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539731832847_0003
18/10/17 01:39:30 INFO impl.YarnClientImpl: Submitted application application_1539731832847_0003
18/10/17 01:39:30 INFO mapreduce.Job: The url to track the job: http://ip-172-31-47-204.eu-west-3.compute.internal:8088/proxy/application_1539731832847_0003/
18/10/17 01:39:30 INFO mapreduce.Job: Running job: job_1539731832847_0003
18/10/17 01:39:36 INFO mapreduce.Job: Job job_1539731832847_0003 running in uber mode : false
18/10/17 01:39:36 INFO mapreduce.Job:  map 0% reduce 0%
18/10/17 01:39:52 INFO mapreduce.Job:  map 11% reduce 0%
18/10/17 01:39:55 INFO mapreduce.Job:  map 33% reduce 0%
18/10/17 01:39:58 INFO mapreduce.Job:  map 38% reduce 0%
18/10/17 01:40:01 INFO mapreduce.Job:  map 51% reduce 0%
18/10/17 01:40:04 INFO mapreduce.Job:  map 56% reduce 0%
18/10/17 01:40:07 INFO mapreduce.Job:  map 66% reduce 0%
18/10/17 01:40:10 INFO mapreduce.Job:  map 68% reduce 0%
18/10/17 01:40:13 INFO mapreduce.Job:  map 72% reduce 0%
18/10/17 01:40:16 INFO mapreduce.Job:  map 73% reduce 0%
18/10/17 01:40:17 INFO mapreduce.Job:  map 74% reduce 0%
18/10/17 01:40:19 INFO mapreduce.Job:  map 79% reduce 0%
18/10/17 01:40:25 INFO mapreduce.Job:  map 85% reduce 0%
18/10/17 01:40:31 INFO mapreduce.Job:  map 92% reduce 0%
18/10/17 01:40:37 INFO mapreduce.Job:  map 99% reduce 0%
18/10/17 01:40:38 INFO mapreduce.Job:  map 100% reduce 0%
18/10/17 01:40:38 INFO mapreduce.Job: Job job_1539731832847_0003 completed successfully
18/10/17 01:40:38 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=592388
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10737418200
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=217310
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=217310
		Total vcore-milliseconds taken by all map tasks=217310
		Total megabyte-milliseconds taken by all map tasks=222525440
	Map-Reduce Framework
		Map input records=107374182
		Map output records=107374182
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1758
		CPU time spent (ms)=125150
		Physical memory (bytes) snapshot=887939072
		Virtual memory (bytes) snapshot=6325460992
		Total committed heap usage (bytes)=950009856
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=230593859918397906
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=10737418200

real	1m11.242s
user	0m4.383s
sys	0m0.202s
[hdfs@ip-172-31-36-240 root]$

[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user/ronniet7626/teragen
Found 5 items
-rw-r--r--   3 hdfs ronniet7626          0 2018-10-17 01:40 /user/ronniet7626/teragen/_SUCCESS
-rw-r--r--   3 hdfs ronniet7626 2684354600 2018-10-17 01:40 /user/ronniet7626/teragen/part-m-00000
-rw-r--r--   3 hdfs ronniet7626 2684354500 2018-10-17 01:40 /user/ronniet7626/teragen/part-m-00001
-rw-r--r--   3 hdfs ronniet7626 2684354600 2018-10-17 01:40 /user/ronniet7626/teragen/part-m-00002
-rw-r--r--   3 hdfs ronniet7626 2684354500 2018-10-17 01:40 /user/ronniet7626/teragen/part-m-00003
[hdfs@ip-172-31-36-240 root]$


Run the terasort command on this file
======================================
Use the time command to report the job's duration
Land the result under your user's home directory
=================================================

[hdfs@ip-172-31-36-240 root]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/ronniet7626/teragen /user/ronniet7626/terasort
18/10/17 01:44:25 INFO terasort.TeraSort: starting
18/10/17 01:44:26 INFO input.FileInputFormat: Total input paths to process : 4
Spent 206ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 211ms
Sampling 10 splits of 320
Making 8 from 100000 sampled records
Computing parititions took 680ms
Spent 893ms computing partitions.
18/10/17 01:44:27 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-47-204.eu-west-3.compute.internal/172.31.47.204:8032
18/10/17 01:44:27 INFO mapreduce.JobSubmitter: number of splits:320
18/10/17 01:44:27 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539731832847_0004
18/10/17 01:44:27 INFO impl.YarnClientImpl: Submitted application application_1539731832847_0004
18/10/17 01:44:27 INFO mapreduce.Job: The url to track the job: http://ip-172-31-47-204.eu-west-3.compute.internal:8088/proxy/application_1539731832847_0004/
18/10/17 01:44:27 INFO mapreduce.Job: Running job: job_1539731832847_0004
18/10/17 01:44:32 INFO mapreduce.Job: Job job_1539731832847_0004 running in uber mode : false
18/10/17 01:44:32 INFO mapreduce.Job:  map 0% reduce 0%
18/10/17 01:44:41 INFO mapreduce.Job:  map 1% reduce 0%
18/10/17 01:44:44 INFO mapreduce.Job:  map 4% reduce 0%
18/10/17 01:44:48 INFO mapreduce.Job:  map 5% reduce 0%
18/10/17 01:44:53 INFO mapreduce.Job:  map 6% reduce 0%
18/10/17 01:44:54 INFO mapreduce.Job:  map 8% reduce 0%
18/10/17 01:44:55 INFO mapreduce.Job:  map 9% reduce 0%
18/10/17 01:45:02 INFO mapreduce.Job:  map 11% reduce 0%
18/10/17 01:45:03 INFO mapreduce.Job:  map 13% reduce 0%
18/10/17 01:45:10 INFO mapreduce.Job:  map 14% reduce 0%
18/10/17 01:45:11 INFO mapreduce.Job:  map 16% reduce 0%
18/10/17 01:45:12 INFO mapreduce.Job:  map 17% reduce 0%
18/10/17 01:45:17 INFO mapreduce.Job:  map 18% reduce 0%
18/10/17 01:45:20 INFO mapreduce.Job:  map 20% reduce 0%
18/10/17 01:45:21 INFO mapreduce.Job:  map 21% reduce 0%
18/10/17 01:45:24 INFO mapreduce.Job:  map 22% reduce 0%
18/10/17 01:45:29 INFO mapreduce.Job:  map 24% reduce 0%
18/10/17 01:45:30 INFO mapreduce.Job:  map 25% reduce 0%
18/10/17 01:45:31 INFO mapreduce.Job:  map 26% reduce 0%
18/10/17 01:45:37 INFO mapreduce.Job:  map 27% reduce 0%
18/10/17 01:45:38 INFO mapreduce.Job:  map 28% reduce 0%
18/10/17 01:45:39 INFO mapreduce.Job:  map 30% reduce 0%
18/10/17 01:45:45 INFO mapreduce.Job:  map 31% reduce 0%
18/10/17 01:45:47 INFO mapreduce.Job:  map 32% reduce 0%
18/10/17 01:45:48 INFO mapreduce.Job:  map 33% reduce 0%
18/10/17 01:45:49 INFO mapreduce.Job:  map 34% reduce 0%
18/10/17 01:45:51 INFO mapreduce.Job:  map 35% reduce 0%
18/10/17 01:45:56 INFO mapreduce.Job:  map 36% reduce 0%
18/10/17 01:45:57 INFO mapreduce.Job:  map 37% reduce 0%
18/10/17 01:45:58 INFO mapreduce.Job:  map 38% reduce 0%
18/10/17 01:45:59 INFO mapreduce.Job:  map 39% reduce 0%
18/10/17 01:46:04 INFO mapreduce.Job:  map 40% reduce 0%
18/10/17 01:46:06 INFO mapreduce.Job:  map 42% reduce 0%
18/10/17 01:46:07 INFO mapreduce.Job:  map 43% reduce 0%
18/10/17 01:46:13 INFO mapreduce.Job:  map 44% reduce 0%
18/10/17 01:46:14 INFO mapreduce.Job:  map 45% reduce 0%
18/10/17 01:46:15 INFO mapreduce.Job:  map 46% reduce 0%
18/10/17 01:46:16 INFO mapreduce.Job:  map 47% reduce 0%
18/10/17 01:46:20 INFO mapreduce.Job:  map 48% reduce 0%
18/10/17 01:46:23 INFO mapreduce.Job:  map 49% reduce 0%
18/10/17 01:46:24 INFO mapreduce.Job:  map 50% reduce 0%
18/10/17 01:46:25 INFO mapreduce.Job:  map 51% reduce 0%
18/10/17 01:46:27 INFO mapreduce.Job:  map 52% reduce 0%
18/10/17 01:46:32 INFO mapreduce.Job:  map 53% reduce 0%
18/10/17 01:46:33 INFO mapreduce.Job:  map 54% reduce 0%
18/10/17 01:46:34 INFO mapreduce.Job:  map 56% reduce 0%
18/10/17 01:46:39 INFO mapreduce.Job:  map 57% reduce 0%
18/10/17 01:46:42 INFO mapreduce.Job:  map 58% reduce 0%
18/10/17 01:46:43 INFO mapreduce.Job:  map 60% reduce 0%
18/10/17 01:46:48 INFO mapreduce.Job:  map 61% reduce 0%
18/10/17 01:46:51 INFO mapreduce.Job:  map 63% reduce 0%
18/10/17 01:46:52 INFO mapreduce.Job:  map 64% reduce 0%
18/10/17 01:46:55 INFO mapreduce.Job:  map 65% reduce 0%
18/10/17 01:47:00 INFO mapreduce.Job:  map 66% reduce 0%
18/10/17 01:47:01 INFO mapreduce.Job:  map 68% reduce 0%
18/10/17 01:47:03 INFO mapreduce.Job:  map 69% reduce 0%
18/10/17 01:47:09 INFO mapreduce.Job:  map 71% reduce 0%
18/10/17 01:47:10 INFO mapreduce.Job:  map 72% reduce 0%
18/10/17 01:47:11 INFO mapreduce.Job:  map 73% reduce 0%
18/10/17 01:47:16 INFO mapreduce.Job:  map 74% reduce 0%
18/10/17 01:47:18 INFO mapreduce.Job:  map 75% reduce 0%
18/10/17 01:47:19 INFO mapreduce.Job:  map 76% reduce 0%
18/10/17 01:47:20 INFO mapreduce.Job:  map 77% reduce 0%
18/10/17 01:47:23 INFO mapreduce.Job:  map 78% reduce 0%
18/10/17 01:47:27 INFO mapreduce.Job:  map 79% reduce 0%
18/10/17 01:47:28 INFO mapreduce.Job:  map 80% reduce 0%
18/10/17 01:47:29 INFO mapreduce.Job:  map 81% reduce 0%
18/10/17 01:47:31 INFO mapreduce.Job:  map 82% reduce 0%
18/10/17 01:47:36 INFO mapreduce.Job:  map 83% reduce 0%
18/10/17 01:47:37 INFO mapreduce.Job:  map 85% reduce 0%
18/10/17 01:47:46 INFO mapreduce.Job:  map 86% reduce 0%
18/10/17 01:47:47 INFO mapreduce.Job:  map 87% reduce 0%
18/10/17 01:47:48 INFO mapreduce.Job:  map 87% reduce 10%
18/10/17 01:47:49 INFO mapreduce.Job:  map 87% reduce 13%
18/10/17 01:47:51 INFO mapreduce.Job:  map 87% reduce 17%
18/10/17 01:47:54 INFO mapreduce.Job:  map 87% reduce 22%
18/10/17 01:47:55 INFO mapreduce.Job:  map 88% reduce 22%
18/10/17 01:47:56 INFO mapreduce.Job:  map 89% reduce 22%
18/10/17 01:48:01 INFO mapreduce.Job:  map 90% reduce 22%
18/10/17 01:48:03 INFO mapreduce.Job:  map 91% reduce 22%
18/10/17 01:48:06 INFO mapreduce.Job:  map 92% reduce 23%
18/10/17 01:48:10 INFO mapreduce.Job:  map 93% reduce 23%
18/10/17 01:48:14 INFO mapreduce.Job:  map 94% reduce 23%
18/10/17 01:48:17 INFO mapreduce.Job:  map 95% reduce 23%
18/10/17 01:48:18 INFO mapreduce.Job:  map 95% reduce 24%
18/10/17 01:48:21 INFO mapreduce.Job:  map 96% reduce 24%
18/10/17 01:48:24 INFO mapreduce.Job:  map 97% reduce 24%
18/10/17 01:48:26 INFO mapreduce.Job:  map 98% reduce 24%
18/10/17 01:48:32 INFO mapreduce.Job:  map 99% reduce 25%
18/10/17 01:48:34 INFO mapreduce.Job:  map 100% reduce 25%
18/10/17 01:48:37 INFO mapreduce.Job:  map 100% reduce 31%
18/10/17 01:48:38 INFO mapreduce.Job:  map 100% reduce 34%
18/10/17 01:48:40 INFO mapreduce.Job:  map 100% reduce 39%
18/10/17 01:48:43 INFO mapreduce.Job:  map 100% reduce 55%
18/10/17 01:48:44 INFO mapreduce.Job:  map 100% reduce 56%
18/10/17 01:48:46 INFO mapreduce.Job:  map 100% reduce 59%
18/10/17 01:48:47 INFO mapreduce.Job:  map 100% reduce 67%
18/10/17 01:48:49 INFO mapreduce.Job:  map 100% reduce 75%
18/10/17 01:48:50 INFO mapreduce.Job:  map 100% reduce 76%
18/10/17 01:48:52 INFO mapreduce.Job:  map 100% reduce 78%
18/10/17 01:48:53 INFO mapreduce.Job:  map 100% reduce 88%
18/10/17 01:48:55 INFO mapreduce.Job:  map 100% reduce 89%
18/10/17 01:48:56 INFO mapreduce.Job:  map 100% reduce 91%
18/10/17 01:48:59 INFO mapreduce.Job:  map 100% reduce 96%
18/10/17 01:49:02 INFO mapreduce.Job:  map 100% reduce 97%
18/10/17 01:49:05 INFO mapreduce.Job:  map 100% reduce 100%
18/10/17 01:49:08 INFO mapreduce.Job: Job job_1539731832847_0004 completed successfully
18/10/17 01:49:08 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4778667899
		FILE: Number of bytes written=9490640937
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10737468760
		HDFS: Number of bytes written=10737418200
		HDFS: Number of read operations=984
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters
		Launched map tasks=320
		Launched reduce tasks=8
		Data-local map tasks=320
		Total time spent by all maps in occupied slots (ms)=2125216
		Total time spent by all reduces in occupied slots (ms)=535848
		Total time spent by all map tasks (ms)=2125216
		Total time spent by all reduce tasks (ms)=535848
		Total vcore-milliseconds taken by all map tasks=2125216
		Total vcore-milliseconds taken by all reduce tasks=535848
		Total megabyte-milliseconds taken by all map tasks=2176221184
		Total megabyte-milliseconds taken by all reduce tasks=548708352
	Map-Reduce Framework
		Map input records=107374182
		Map output records=107374182
		Map output bytes=10952166564
		Map output materialized bytes=4662846852
		Input split bytes=50560
		Combine input records=0
		Combine output records=0
		Reduce input groups=107374182
		Reduce shuffle bytes=4662846852
		Reduce input records=107374182
		Reduce output records=107374182
		Spilled Records=214748364
		Shuffled Maps =2560
		Failed Shuffles=0
		Merged Map outputs=2560
		GC time elapsed (ms)=43935
		CPU time spent (ms)=1195990
		Physical memory (bytes) snapshot=166452953088
		Virtual memory (bytes) snapshot=518918193152
		Total committed heap usage (bytes)=189554229248
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=10737418200
	File Output Format Counters
		Bytes Written=10737418200
18/10/17 01:49:08 INFO terasort.TeraSort: done

real	4m43.914s
user	0m6.932s
sys	0m0.270s

Land result in users home directory:
====================================

[hdfs@ip-172-31-36-240 root]$ hdfs dfs -ls /user/ronniet7626/terasort
Found 10 items
-rw-r--r--   1 hdfs ronniet7626          0 2018-10-17 01:49 /user/ronniet7626/terasort/_SUCCESS
-rw-r--r--  10 hdfs ronniet7626         77 2018-10-17 01:44 /user/ronniet7626/terasort/_partition.lst
-rw-r--r--   1 hdfs ronniet7626 1341324400 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00000
-rw-r--r--   1 hdfs ronniet7626 1321377000 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00001
-rw-r--r--   1 hdfs ronniet7626 1344586900 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00002
-rw-r--r--   1 hdfs ronniet7626 1351892700 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00003
-rw-r--r--   1 hdfs ronniet7626 1349175000 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00004
-rw-r--r--   1 hdfs ronniet7626 1362008100 2018-10-17 01:48 /user/ronniet7626/terasort/part-r-00005
-rw-r--r--   1 hdfs ronniet7626 1323208300 2018-10-17 01:49 /user/ronniet7626/terasort/part-r-00006
-rw-r--r--   1 hdfs ronniet7626 1343845800 2018-10-17 01:49 /user/ronniet7626/terasort/part-r-00007
[hdfs@ip-172-31-36-240 root]$



















