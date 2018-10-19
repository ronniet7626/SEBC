Command and output for hdfs dfs -ls /user
==========================================

hdfs@ip-172-31-41-159 centos]$ hdfs dfs -ls /user
Found 5 items
drwxr-xr-x   - fullerton fullerton          0 2018-10-19 09:23 /user/fullerton
drwxrwxrwx   - mapred    hadoop             0 2018-10-19 09:20 /user/history
drwxrwxr-t   - hive      hive               0 2018-10-19 09:23 /user/hive
drwxrwxr-x   - hue       hue                0 2018-10-19 09:24 /user/hue
drwxr-xr-x   - raffles   raffles            0 2018-10-19 09:23 /user/raffles



The output from the CM API call ../api/v14/hosts
=================================================

root@ip-172-31-37-49 cloudera-scm-server]# curl -u admin:admin http://localhost:7180/api/v14/users
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ]
  } ]
}

