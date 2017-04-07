# Kafka basic commands

You will find all programms in bin dir. Tested under [Apache Kafka](https://kafka.apache.org/) version 0.9.
Variables are in brackets like {varname}


## Kafka Broker start / stop ##

Kafka uses config from ../config/server.properties

**command:** kafka start <br>
**command:** kafka stop <br>
**command:** kafka status <br>

## Create topic ##

**command:**
>./kafka-topics.sh --create --topic {topic_name} --replication-factor {#replication-factor} --partitions {#partition} --zookeeper {host}:{port}

**example:**
>./kafka-topics.sh --create --topic topic_name --replication-factor 1 --partitions 10 --zookeeper localhost:2181

**options:**
--config retention.bytes={#bytes} retention.ms={#ms}

**expected result:**  
```
Created topic "topic_name".
```

## List all topics ##

**command:**
>./kafka-topics.sh --list --zookeeper  {host}:{port}

**example:**
>./kafka-topics.sh --list --zookeeper  localhost:2181

**expected result:**
```
topic_name
```

## Delete a topic ##

**command:**
>./kafka-topics.sh --zookeeper {host}:{port} --delete --topic {topic_name}

**example:**
> ./kafka-topics.sh --zookeeper localhost:2181 --delete --topic topic_name

**expected result:**
```

```

## Describe a topic ##

**command:**
>./kafka-topics.sh --describe --zookeeper {host}:{port} --topic {topic_name}

**example:**
>./kafka-topics.sh --describe --zookeeper localhost:2181 --topic topic_name

**expected result:**
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

**command:**
>./kafka-console-consumer.sh --bootstrap-server {host}:{port} --topic {topic_name} --new-consumer

**example:**
>./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic topic_name --new-consumer

**options:** If security is active use: --security-protocol {SASL_SSL} xor {SASL_PLAINTEXT} xor {SSL} else: default {PLAINTEXT} <br>
									  : --consumer.config ./config/client-security.properties // See below for client-security.properties <br>
									    --from-beginning //read all messages from beginning
**expected result:** <br>
```

```

## Consolen producer ##

**command:**
>./kafka-console-producer.sh --broker-list {host}:{port} --topic {topic_name} --new-producer

**example:**
>./kafka-console-producer.sh --broker-list localhost:9092 --topic topic_name  --new-producer

**options:**
If security is active use: --security-protocol {SASL_SSL} xor {SASL_PLAINTEXT} xor {SSL} else: default {PLAINTEXT} <br>
							          : --producer.config ./config/producer.properties // See below for client-security.properties <br>
**expected result:** <br>
```{put your messages hier and return}

```

## Show active consumer groups ##

**command:**
>./kafka-run-class.sh kafka.admin.ConsumerGroupCommand --list --new-consumer --bootstrap-server {host}:{port}

**example:**
>./kafka-run-class.sh kafka.admin.ConsumerGroupCommand --list --new-consumer --bootstrap-server localhost:9092

**expected result:** <br>
```

```

## Show current active consumer offset and consumer LAG ##

**command:**
>./kafka-run-class.sh kafka.admin.ConsumerGroupCommand --describe --new-consumer --bootstrap-server {host}:{port} --group group_name

**example:**
>./kafka-run-class.sh kafka.admin.ConsumerGroupCommand --describe --new-consumer --bootstrap-server localhost:9092 --group group_name

**expected result:** <br>
```

```

## Show internal topic ##

**command:**
>
**example:**
>
**expected result:**
```

```

## Add partitions to an existing topic ##

**command:**
>./kafka-topics.sh --alter --zookeeper {host}:{port} --topic {topic_name} --partitions {#partitions}

**example:**
>./kafka-topics.sh --alter --zookeeper localhost:2181 --topic topic_name --partitions 4

**expected result:** <br>
```

```

## Config for client-security.properties ##
```

```

## Config for producer.properties ##
```

```
