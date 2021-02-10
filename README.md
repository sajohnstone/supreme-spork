# A simple Kafka Cluster

This uses docker compose to create a simple Kafka cluster with 3 kafka brokers and a single ZooKeeper instance.

## Getting started

Run the following

```bash
docker-compose up
```

## Access things

To access the [Kafdrop](https://github.com/obsidiandynamics/kafdrop) console go to <http://localhost:9000>

## Console quick guide

Probably the easiest way to get onto the console it to use a docker exec command

```bash
docker exec -it b16dfcb268aa /bin/sh     
```

from within the console we can:-

```bash
#will create a new topic called 'test-topic'
kafka-topics --zookeeper zookeeper:2181 --topic test-topic --create --partitions=3 --replication-factor=2 
## show all topics
kafka-topics --zookeeper zookeeper:2181 --list
## show details for 'test-topic'
kafka-topics --zookeeper zookeeper:2181 --topic test-topic --describe
## delete 'test-topic'
kafka-topics --zookeeper zookeeper:2181 --topic test-topic --delete
```
