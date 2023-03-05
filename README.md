MongoDB cluster
===============

Ansible role for MongoDB cluster installation & configuration.


Requirements
------------

 - RHEL7-based OS;
 - designed for 7 servers;
 - python3.6 or higher.


Variables
---------

|      Name      |        Description        | Default Value |
|----------------|---------------------------|---------------|
| mongo_version  | database version          | 5.0           |
| mongo_database | database name             | CHANGEME      |
| mongodb_user   | database username         | CHANGEME      |
| mongodb_pass   | databasepassword          | CHANGEME      |
| mongodb_role   | database role             | CHANGEME      |
| ip01           | node ip (primary replica) | CHANGEME      |
| ip02           | node ip (replica)         | CHANGEME      |
| ip03           | node ip (replica)         | CHANGEME      |
| ip04           | node ip (primary shard)   | CHANGEME      |
| ip05           | node ip (shard)           | CHANGEME      |
| ip06           | node ip (shard)           | CHANGEME      |
| ip07           | node ip (router)          | CHANGEME      |


Tags
----

Supported tags in tasks:

 - pretasks
 - primary_replica
 - ssl
 - replicas
 - replication
 - primary_shard
 - shards_hosts
 - shards
 - router


License
-------

BSD-3-Clause


Author Information
------------------

https://github.com/Borodatko
