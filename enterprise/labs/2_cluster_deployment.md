[root@ip-172-31-43-254 tmp]#  curl -u admin:admin 'http://localhost:7180/api/v2/cm/deployment'
{
  "timestamp" : "2018-10-17T11:22:39.031Z",
  "clusters" : [ {
    "name" : "ronniet7626",
    "version" : "CDH5",
    "services" : [ {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "3"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3517"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4848"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "UhLR5jLzQBHRhBqL3xNaJT8MeLPaed"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bhlhqtzqv626k23or5pt9od12"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2a9f0lqo7870hye9hy06abpuf"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-4ba9d57bd61506784585100e82f64d6e",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7v3gtnj6pd04mh6kmlgk63sz8"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "976byjj9ziui3eo56x1jl514c"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-cb825c2cb01a755cd981df5b4664e357",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3trzv5ov3cipdu5h7hv4bkz8x"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-4ba9d57bd61506784585100e82f64d6e",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "31"
          }, {
            "name" : "role_jceks_password",
            "value" : "54u1sygyg0ztuvcd3y45uhq3c"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "3220069990"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "PwV6v8kDOSM4LJgFst8WO0wwiOu83e"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "IfSM8Fj6CRyREh37EB4UPelbJsD1Jq"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "mUCMEKJlyOhweRI8rJokiNGhqtP6hx"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-cb825c2cb01a755cd981df5b4664e357",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cgft7p1z3odq7ufdidajhje77"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-4ba9d57bd61506784585100e82f64d6e",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "di1ztha692hajqngmlkuudcr5"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1qog9mkrbq9mace4upepxt4j7"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-cb825c2cb01a755cd981df5b4664e357",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "apeaz8qjok747pqlnahtoz499"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cxo7yg6jsi6cc23ueqnu1c4uw"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-4ba9d57bd61506784585100e82f64d6e",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "904wxjbn7o18xxvfko63n0cpd"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bjzly1rbs3uyyevdi9q19xvm2"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4tp7fodt29gl4shh78hmqa6e4"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-cb825c2cb01a755cd981df5b4664e357",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4ucq5ac2zh8h6f2o7mgzy7ibf"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "33"
          }, {
            "name" : "role_jceks_password",
            "value" : "23izjyfokwj52ezfag7gujewo"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-4ba9d57bd61506784585100e82f64d6e",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "45"
          }, {
            "name" : "role_jceks_password",
            "value" : "auqb3bnh6i4ufp99bi0egn9do"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "52428800"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-088ece6ed0ab066fd9ab25d061723b0e",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "38r23v9tysqmqcqd1bubiaixu"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "aa0qmeih7vo4r94fgusqap37c"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-cb825c2cb01a755cd981df5b4664e357",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5nt348rwkllk6ex5otdrebc11"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "52428800"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "52428800"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "912680550"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "153"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-43-254.eu-west-3.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "training"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-d87e2f1454fbbb2801fb7a561177dcf8",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "tdkby8axtmphlgu6ut2kbv2l"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-8c45c3eff059070c99bff93a07a0b70a",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ah1y6atztdz7j3of8dne4klsp"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "e706d6a6-03f0-45f7-884f-9591c33be112",
    "ipAddress" : "172.31.36.240",
    "hostname" : "ip-172-31-36-240.eu-west-3.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9",
    "ipAddress" : "172.31.43.254",
    "hostname" : "ip-172-31-43-254.eu-west-3.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "3f2b8d01-f3e0-4b60-9b4f-93d689b3f9fd",
    "ipAddress" : "172.31.43.41",
    "hostname" : "ip-172-31-43-41.eu-west-3.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "5b7bcebe-026f-41c6-9fbb-5d8b77ce54b2",
    "ipAddress" : "172.31.44.13",
    "hostname" : "ip-172-31-44-13.eu-west-3.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "d0a695bc-e19f-4db5-b41b-e67c52b3aeb7",
    "ipAddress" : "172.31.47.204",
    "hostname" : "ip-172-31-47-204.eu-west-3.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "dada813602a7f93f2e607b590d9c606801d94b5fa295539bcdff75e502d130d0",
    "pwSalt" : 2481504557740625782,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-d87e2f1454fbbb2801fb7a561177dcf8",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "be32c96695df73bf6cf0aa6a02d7d613dd54d74b21b54d39764fbb3304945b61",
    "pwSalt" : -7953367919438380209,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b8439adae642142da4ea9e4f98aaeab004d6c8a1cbabdd5115101d9b2e2ab17d",
    "pwSalt" : 4786030916821585957,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-d87e2f1454fbbb2801fb7a561177dcf8",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "5e6fd8de1c8e07d38000a5792801c863744bdf58e6ca73658f8223b5ed0aa869",
    "pwSalt" : -5061936747728454410,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b900952933e6f553fb02741fb1c7301b24675f186fc76c4a618d7e97ef560659",
    "pwSalt" : 6341955790635882235,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "866ecbc208d69ad35f592155e83bd9412aa763ec2e1e63e6834b8f168f61ab0f",
    "pwSalt" : -2546713405606191125,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "5745260cd9c7c3e08b7d91a788607b00a85fa553a22f2017469036e86f623b24",
    "pwSalt" : 1190080518986878429,
    "pwLogin" : true
  }, {
    "name" : "ronniet7626",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "17dd3edd760a80318807c21a549e8d09bbaba6352da1c48fb9e229c8318023aa",
    "pwSalt" : 7150224468540591779,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.13.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20180328-1830",
    "gitHash" : "f90c58536c252d70a23bde6d94514d92a1f111d4",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "ip-172-31-43-254.eu-west-3.compute.internal"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "training"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-43-254.eu-west-3.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "training"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "6442450944"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "19cneewvl0lob7t42bqnaut4h"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "43wunp5d72tb6ifnowxz52nln"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "7xtmxgi8b8u89bz9de1vvk7z5"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "4egg3l5odpgp2jnhy2mv3s6hr"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "b967te9fohyrn1qxmlvpznod5"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-d87e2f1454fbbb2801fb7a561177dcf8",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "e4117ec0-3a92-4e9f-bb7e-584bb28a21a9"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9a8jlw7cnktw5b6n2fsdbnwqe"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/27/2012 2:20"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://172.31.43.254/CDH5/"
    } ]
  }
}[root@ip-172-31-43-254 tmp]#