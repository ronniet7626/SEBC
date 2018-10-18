What is ubertask optimization?
===============================

Ubertask optimisation runs “sufficiently small” jobs sequentially within a single JVM. This property can be changed in Performance category. Property name is mapreduce.job.ubertask.enable

Other configuration options are:

Ubertask Maximum Maps
mapreduce.job.ubertask.maxmaps

Ubertask Maximum Reduces
mapreduce.job.ubertask.maxreduces

Ubertask Maximum Job Size
mapreduce.job.ubertask.maxbytes

Where in CM is the Kerberos Security Realm value displayed?
============================================================

Administration -> Settings -> Kerberos -> Kerberos Security Realm. The default one is HADOOP.COM

Kerberos Security Realm
default_realm

Which CDH service(s) host a property for enabling Kerberos authentication?
===========================================================================

Search for "kerberos principal" in search bar to show a list of services available for Kerberos authentication.
On my cluster the following CDH options are available

Zookeeper Kerberos Principal
HDFS Kerberos Principal
YARN Kerberos Principal

CM options available are:

Cloudera Manager Service Activity Monitor Kerberos Principal
Cloudera Manager Service Resource Manager Kerberos Principal
Cloudera Manager Service Navigator Kerberos Principal

How do you upgrade the CM agents?
==================================

First upgrade the cloudera manager Server manually. Once the CM server is upgraded and restarted use the wizard to upgrade the cloudera manager agents and optionally the JDK.

Give the tsquery statement used to chart Hue's CPU utilization?
=================================================================

select cpu_system_rate + cpu_user_rate where category=ROLE and serviceType = HUE

Name all the roles that make up the Hive service
=================================================

Gateway
Hive Metastore Server
HiveServer2
WebHcat Server




What steps must be completed before integrating Cloudera Manager with Kerberos?
=================================================================================

Go to Administration -> Security, there is Security inspector which should be run before Kerberos setup. Also, at first pages of Kerberos wizard there is a number of steps that require confirmation that they have been completed, before the wizard will run.

Install KDC (MIT)
Create Kerberos Principal for the Cloudera Manager Server
Ensure KDC allows renewable tickets
Java security extention library installed




