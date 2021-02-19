Burrow Role
===========

Role for run Burrow in docker-compose as a single monitoring tool for keeping track of consumer lag Apache Kafka.  
Role supports multiple Kafka Cluster.  

Requirements
------------

- At least one kafka cluster.
- Docker installed on target host.

Role Variables
--------------

In common way you should redefine only one dict , ` burrow_clusters `.

```yml
burrow_clusters:

  - name: "my_cluster_one"
    kafka_hosts:
      - kafka-cluster_one-01:9092
      - kafka-cluster_one-02:9092
      - kafka-cluster_one-03:9092
    zookeeper_hosts:
      - zookeeper-cluster_one-01:2181
      - zookeeper-cluster_one-02:2181
      - zookeeper-cluster_one-03:2181

  - name: "my_cluster_two"
    kafka_hosts:
      - kafka-cluster_two-01:9092
      - kafka-cluster_two-02:9092
      - kafka-cluster_two-03:9092
    zookeeper_hosts:
      - zookeeper-cluster_two-01:2181
      - zookeeper-cluster_two-02:2181
      - zookeeper-cluster_two-03:2181 

```


Example Playbook
----------------

```yml
- hosts: burrow
  gather_facts: yes
  become: yes
  roles:
    - { role: burrow-docker-compose, tags: burrow }
```
