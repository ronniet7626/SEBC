Write curl statements that stop, start, and check the current state of your Hive service.
Add these statements and their output to enterprise/labs/3_api_hive_state.md
==========================================================================================

STATUS
=======


curl -k -u 'admin:admin' 'http://localhost:7180/api/v2/clusters/ronniet7626/services/hive/'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-43-254.eu-west-3.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"


STOP
====

curl -X POST -u admin:admin -w "\n" http://localhost:7180/api/v2/clusters/ronniet7626/services/hive/commands/stop
{
  "id" : 405,
  "name" : "Stop",
  "startTime" : "2018-10-17T11:39:02.970Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}

STATUS
======

curl -k -u 'admin:admin' 'http://localhost:7180/api/v2/clusters/ronniet7626/services/hive/'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-43-254.eu-west-3.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STOPPED",
  "healthSummary" : "DISABLED",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "DISABLED"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "DISABLED"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"


  
  START
  =====

  curl X POST -u admin:admin -w "\n" http://localhost:7180/api/v2/clusters/ronniet7626/services/hive/commands/start
{
  "id" : 409,
  "name" : "Start",
  "startTime" : "2018-10-17T11:40:52.130Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}

STATUS
======

root@ip-172-31-43-254 tmp]# curl -k -u 'admin:admin' 'http://localhost:7180/api/v2/clusters/ronniet7626/services/hive/'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-43-254.eu-west-3.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "DISABLED",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "DISABLED"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "DISABLED"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"