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
docker exec -it 1ee3f7eff146 /bin/sh     
```

## Common topics command

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

## Producer and consumer cli commands

```bash
#create a message(s) to the topic (CTRL C to exit)
kafka-console-producer --topic test-topic --broker-list kafka1:19091,kafka2:19092,kafka3:19093
#create a message(s) to the topic with ACKS=All (CTRL C to exit)
kafka-console-producer --topic test-topic --broker-list kafka1:19091,kafka2:19092,kafka3:19093 --producer-property acks=all
#consume test-topic (from the begining).  Note is will carry on consuming if you add more messages
kafka-console-consumer --topic test-topic --from-beginning --bootstrap-server kafka1:19091,kafka2:19092,kafka3:19093 
```
