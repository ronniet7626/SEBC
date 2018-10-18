```
Verify user privileges
======================
```
[root@ip-172-31-36-240 ~]# beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181018103939_0a508aae-ea0e-4a68-a062-8f8f384b4e16): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018103939_0a508aae-ea0e-4a68-a062-8f8f384b4e16); Time taken: 0.586 seconds
INFO  : Executing command(queryId=hive_20181018103939_0a508aae-ea0e-4a68-a062-8f8f384b4e16): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018103939_0a508aae-ea0e-4a68-a062-8f8f384b4e16); Time taken: 0.287 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.17 seconds)
0: jdbc:hive2://localhost:10000/default>


Create a Sentry role with full authorization
==============================================

0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181018125151_658f4bc0-60a3-4760-b5f8-6455e8acd1c6): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018125151_658f4bc0-60a3-4760-b5f8-6455e8acd1c6); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20181018125151_658f4bc0-60a3-4760-b5f8-6455e8acd1c6): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018125151_658f4bc0-60a3-4760-b5f8-6455e8acd1c6); Time taken: 0.189 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.355 seconds)

CREATE NEW USERS
================

[root@ip-172-31-43-254 krb5kdc]# kadmin.local
Authenticating as principal ronniet7626/admin@PUNEETHA.COM with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@PUNEETHA.COM; defaulting to no policy
Enter password for principal "george@PUNEETHA.COM":
Re-enter password for principal "george@PUNEETHA.COM":
Principal "george@PUNEETHA.COM" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@PUNEETHA.COM; defaulting to no policy
Enter password for principal "ferdinand@PUNEETHA.COM":
Re-enter password for principal "ferdinand@PUNEETHA.COM":
Principal "ferdinand@PUNEETHA.COM" created.
kadmin.local:  exit


Create test roles
=================
0: jdbc:hive2://localhost:10000/default> create role writes;
INFO  : Compiling command(queryId=hive_20181018130101_da03dd0c-64ea-4c98-ac8c-8ee07e929b13): create role writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130101_da03dd0c-64ea-4c98-ac8c-8ee07e929b13); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20181018130101_da03dd0c-64ea-4c98-ac8c-8ee07e929b13): create role writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130101_da03dd0c-64ea-4c98-ac8c-8ee07e929b13); Time taken: 0.007 seconds
INFO  : OK
No rows affected (0.07 seconds)
0: jdbc:hive2://localhost:10000/default> grant select on database default to rolw reads;
Error: Error while compiling statement: FAILED: ParseException line 1:36 cannot recognize input near 'rolw' 'reads' '<EOF>' in user|group|role name (state=42000,code=40000)
0: jdbc:hive2://localhost:10000/default> grant role reads to group selector;
INFO  : Compiling command(queryId=hive_20181018130202_509e3feb-175c-42c5-a880-9bbca7770cd9): grant role reads to group selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130202_509e3feb-175c-42c5-a880-9bbca7770cd9); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20181018130202_509e3feb-175c-42c5-a880-9bbca7770cd9): grant role reads to group selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130202_509e3feb-175c-42c5-a880-9bbca7770cd9); Time taken: 0.041 seconds
INFO  : OK
No rows affected (0.111 seconds)

0: jdbc:hive2://localhost:10000/default> show roles;
INFO  : Compiling command(queryId=hive_20181018130505_85e13075-4187-4181-9a46-4620fcfa4207): show roles
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:role, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130505_85e13075-4187-4181-9a46-4620fcfa4207); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20181018130505_85e13075-4187-4181-9a46-4620fcfa4207): show roles
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130505_85e13075-4187-4181-9a46-4620fcfa4207); Time taken: 0.025 seconds
INFO  : OK
+---------------+--+
|     role      |
+---------------+--+
| reads         |
| sentry_admin  |
| writes        |
| admin_role    |
+---------------+--+
4 rows selected (0.12 seconds)

Grant read privilege for all tables to reads
=============================================

0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20181018130606_75476c88-28a8-4a4c-9248-3cf9d808202a): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130606_75476c88-28a8-4a4c-9248-3cf9d808202a); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20181018130606_75476c88-28a8-4a4c-9248-3cf9d808202a): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130606_75476c88-28a8-4a4c-9248-3cf9d808202a); Time taken: 0.045 seconds
INFO  : OK
No rows affected (0.11 seconds)

0: jdbc:hive2://localhost:10000/default> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20181018130707_8b8d85bd-ca1c-455c-bc1d-6eda43b07311): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130707_8b8d85bd-ca1c-455c-bc1d-6eda43b07311); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20181018130707_8b8d85bd-ca1c-455c-bc1d-6eda43b07311): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130707_8b8d85bd-ca1c-455c-bc1d-6eda43b07311); Time taken: 0.012 seconds
INFO  : OK
No rows affected (0.08 seconds)

Grant read privilege for default.sample07 only to 'writes':
============================================================
0: jdbc:hive2://localhost:10000/default> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20181018130808_e78cb5af-bcbf-4d0d-8914-17954d966318): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130808_e78cb5af-bcbf-4d0d-8914-17954d966318); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20181018130808_e78cb5af-bcbf-4d0d-8914-17954d966318): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130808_e78cb5af-bcbf-4d0d-8914-17954d966318); Time taken: 0.039 seconds
INFO  : OK
No rows affected (0.103 seconds)

0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20181018130808_9ba9c2c9-4ea1-455f-b720-28c5ffc7b837): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130808_9ba9c2c9-4ea1-455f-b720-28c5ffc7b837); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20181018130808_9ba9c2c9-4ea1-455f-b720-28c5ffc7b837): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130808_9ba9c2c9-4ea1-455f-b720-28c5ffc7b837); Time taken: 0.012 seconds
INFO  : OK
No rows affected (0.076 seconds)


0: jdbc:hive2://localhost:10000/default> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20181018130909_1b5485a1-00b7-4272-b4d6-2f7ccd937526): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018130909_1b5485a1-00b7-4272-b4d6-2f7ccd937526); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20181018130909_1b5485a1-00b7-4272-b4d6-2f7ccd937526): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018130909_1b5485a1-00b7-4272-b4d6-2f7ccd937526); Time taken: 0.01 seconds
INFO  : OK
No rows affected (0.075 seconds)


kinit as george, then login to beeline
=======================================

[george@ip-172-31-36-240 centos]$ klist
Ticket cache: FILE:/tmp/krb5cc_1100
Default principal: george@PUNEETHA.COM

Valid starting     Expires            Service principal
18/10/18 13:10:27  19/10/18 13:10:27  krbtgt/PUNEETHA.COM@PUNEETHA.COM
	renew until 25/10/18 13:10:27

[george@ip-172-31-36-240 centos]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
scan complete in 1ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181018131919_1f3f19bd-ca41-4f16-b3da-570b978d3f47): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018131919_1f3f19bd-ca41-4f16-b3da-570b978d3f47); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20181018131919_1f3f19bd-ca41-4f16-b3da-570b978d3f47): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018131919_1f3f19bd-ca41-4f16-b3da-570b978d3f47); Time taken: 0.102 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.238 seconds)

kinit as ferdinand, then login to beeline
=========================================


[ferdinand@ip-172-31-36-240 centos]$ kinit ferdinand
Password for ferdinand@PUNEETHA.COM:
[ferdinand@ip-172-31-36-240 centos]$ klist
Ticket cache: FILE:/tmp/krb5cc_1200
Default principal: ferdinand@PUNEETHA.COM

Valid starting     Expires            Service principal
18/10/18 13:21:48  19/10/18 13:21:48  krbtgt/PUNEETHA.COM@PUNEETHA.COM
	renew until 25/10/18 13:21:48


ferdinand@ip-172-31-36-240 centos]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
scan complete in 1ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-36-240.eu-west-3.compute.internal@PUNEETHA.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181018132222_984a7437-6ecd-4e10-a54c-aa809974d21e): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018132222_984a7437-6ecd-4e10-a54c-aa809974d21e); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20181018132222_984a7437-6ecd-4e10-a54c-aa809974d21e): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018132222_984a7437-6ecd-4e10-a54c-aa809974d21e); Time taken: 0.098 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.233 seconds)






