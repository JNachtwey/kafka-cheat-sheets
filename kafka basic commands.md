# Kafka basic commands

You will find all programms in bin dir. Tested under apache kafka version 0.9. [Apache Kafka](https://kafka.apache.org/)
Variables are in brackets like {varname}


## Kafka Broker start / stop ##

Kafka uses config from ../config/server.properties

**command:** kafka start <br>
**command:** kafka stop <br>
**command:** kafka status <br>

## Create topic ##

**command:** ./kafka-topics.sh --create --topic {topic_name} --replication-factor {#replication-factor} --partitions {#partition} --zookeeper {host}:{port} <br>
**example:** ./kafka-topics.sh --create --topic topic_name --replication-factor 1 --partitions 10 --zookeeper localhost:2181 <br>
**expected result:**  
```
Created topic "topic_name".
```

## List all topics ##

**command:** ./kafka-topics.sh --list --zookeeper  {host}:{port} <br>
**example:** ./kafka-topics.sh --list --zookeeper  localhost:2181 <br>
**expected result:** 
```
topic_name

```

## Delete a topic ##

**command:** <br>
**example:** <br>
**expected result:** <br> 
```

```

## Describe a topic ##

**command:** ./kafka-topics.sh --describe --zookeeper {host}:{port} --topic {topic_name} <br>
**example:** ./kafka-topics.sh --describe --zookeeper localhost:2181 --topic topic_name <br>
**expected result:** <br>
```
Topic:topic_name   PartitionCount:10       ReplicationFactor:1     Configs:
        Topic: topic_name  Partition: 0    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 1    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 2    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 3    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 4    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 5    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 6    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 7    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 8    Leader: 0       Replicas: 0     Isr: 0
        Topic: topic_name  Partition: 9    Leader: 0       Replicas: 0     Isr: 0
```

## Consolen consumer ##

**command:** <br>
**example:** <br>
**options:** If security is active use: --security-protocol {SASL_SSL} xor {SASL_PLAINTEXT} xor {SSL} else: default {PLAINTEXT}
									  : --consumer.config ./config/client-security.properties // See below for client-security.properties
**expected result:** <br>
```

```

## Consolen producer ##

**command:** ./kafka-console-producer.sh --broker-list {host}:{port} --topic {topic_name} --new-producer<br>
**example:** ./kafka-console-producer.sh --broker-list localhost:9092 --topic topic_name  --new-producer<br>
**options:** If security is active use: --security-protocol {SASL_SSL} xor {SASL_PLAINTEXT} xor {SSL} else: default {PLAINTEXT}
							          : --producer.config ./config/producer.properties // See below for client-security.properties
**expected result:** <br>
```{put your messages hier and return}

```

## Show active consumer groups ##

**command:** <br>
**example:** <br>
**expected result:** <br> 
```

```

## Show current active consumer offset and consumer LAG ##

**command:** <br>
**example:** <br>
**expected result:** <br> 
```

```

## Show internal topic __TODO ##

**command:** <br>
**example:** <br>
**expected result:** <br> 
```

```

## Add partitions to an existing topic ##

**command:** <br>
**example:** <br>
**expected result:** <br> 
```

```

## Config for client-security.properties ##
```

```

## Config for producer.properties ##
```

```