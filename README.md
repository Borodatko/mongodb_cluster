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

 - **pretasks**
 - **primary_replica**
 - **ssl**
 - **replicas**
 - **replication**
 - **primary_shard**
 - **shards_hosts**
 - **shards**
 - **router**


Example of inventory file
-------------------------

```yaml
---
all:
  hosts:
    mongo01:
      ansible_host: CHANGEME
    mongo02:
      ansible_host: CHANGEME
    mongo03:
      ansible_host: CHANGEME
    mongo04:
      ansible_host: CHANGEME
    mongo05:
      ansible_host: CHANGEME
    mongo06:
      ansible_host: CHANGEME
    mongo07:
      ansible_host: CHANGEME
primary_replica:
  hosts:
    mongo01:
      ansible_host: CHANGEME
replias:
  hosts:
    mongo01:
      ansible_host: CHANGEME
    mongo02:
      ansible_host: CHANGEME
    mongo03:
      ansible_host: CHANGEME
primary_shard:
  hosts:
    mongo04:
      ansible_host: CHANGEME
shards:
  hosts:
    mongo04:
      ansible_host: CHANGEME
    mongo05:
      ansible_host: CHANGEME
    mongo06:
      ansible_host: CHANGEME
router:
  hosts:
    mongo07:
      ansible_host: CHANGEME

cluster:
  children:
    all:
    primary_replica:
    replias:
    primary_shard:
    shards:
    router:
  vars:
    ansible_user: CHANGEME
    ansible_python_interpreter: /usr/bin/python3.6
...
```


Example Playbook
----------------

An example of using role:

```yaml
- name: MongoDB Provisioning
  hosts:
    all,primary_replica,replias,primary_shard,shards,router
  roles:
    - mongodb-cluster
```


License
-------

BSD-3-Clause


Author Information
------------------

https://github.com/Borodatko
