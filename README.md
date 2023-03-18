MongoDB sharded cluster
=======================

Ansible role for MongoDB sharded cluster installation & configuration.

Cluster consists of:

 - 3 Config servers
 - 3 Shards
 - 1 Router


Requirements
------------

 - RHEL7-based OS;
 - python3.6 or higher.


WARNING
-------

Parted module is used in role, which has unmaintained Ansible documentation.

https://docs.ansible.com/archive/ansible/2.3/parted_module.html


Variables
---------

|      Name      |        Description              | Default Value |
|----------------|---------------------------------|---------------|
| blockDevice    | block device                    | /dev/sdb      |
| partedDevice   | partition                       | /dev/sdb1     |
| mongoDir       | database storage path           | /mongo        |
| mongo_version  | database version                | 5.0           |
| mongo_database | database name                   | CHANGEME      |
| mongodb_user   | database username               | CHANGEME      |
| mongodb_pass   | databasepassword                | CHANGEME      |
| mongodb_role   | database role                   | CHANGEME      |
| host01         | primary config replica hostname | mongo01       |
| host02         | config replica node hostname    | mongo02       |
| host03         | config replica node hostname    | mongo03       |
| host04         | primary shard hostname          | mongo04       |
| host05         | shard node hostname             | mongo05       |
| host06         | shard node hostname             | mongo06       |
| host07         | mongos router hostname          | mongo07       |
| ip01           | primary config replica ip addr  | CHANGEME      |
| ip02           | config replica node ip addr     | CHANGEME      |
| ip03           | config replica node ip addr     | CHANGEME      |
| ip04           | primary shard ip addr           | CHANGEME      |
| ip05           | shard node ip addr              | CHANGEME      |
| ip06           | shard node ip addr              | CHANGEME      |
| ip07           | mongos router ip addr           | CHANGEME      |


Tags
----

Supported tags in tasks:

 - **mongo**
 - **pretasks**
 - **xfs**
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
---
- name: MongoDB Provisioning
  hosts: all,primary_replica,replias,primary_shard,shards,router
  roles:
    - mongodb_cluster
...
```


License
-------

BSD-3-Clause


Author Information
------------------

https://github.com/Borodatko
