Use the API on the command line to:
Report the latest available version of the API
================================================

curl -u admin:admin http://localhost:7180/api/version
v19

Report the CM version
======================

curl -u admin:admin http://localhost:7180/api/v14/cm/version
{
  "version" : "5.14.4",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20180707-0445",
  "gitHash" : "0971e84bdceb60db9b96533f46451f40ed8cbdf9",
  "snapshot" : false
}

List all CM users
==================

curl -u admin:admin http://localhost:7180/api/v14/users
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "ronniet7626",
    "roles" : [ "ROLE_LIMITED" ]
  } ]
}

Report the database server in use by CM
=======================================

curl -u admin:admin http://localhost:7180/api/v14/cm/scmDbInfo
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
