# Kafka performance testing #

You will find all programms in bin dir. Tested under apache kafka version 0.9. [Apache Kafka](https://kafka.apache.org/)
Variables are in brackets like <varname>


## Consumer Perfomance ##

**command:** ./kafka-consumer-perf-test.sh --batch-size <batch-size> --broker-list <host>:<port> --group <group_name> --new-consumer 
**example:** ./kafka-consumer-perf-test.sh --batch-size 1000 --broker-list localhost:9092 --group group_name --new-consumer
**expected result: ** 
```

```

## Producer Perfomance ##

### option 1: ###

**command: **./kafka-run-class.sh org.apache.kafka.tools.ProducerPerformance --topic <topic_name> --num-records  <#num-records> --record-size <record-size> --throughput <testing> --producer-props bootstrap.servers=<host>:<port>
**example: **./kafka-run-class.sh org.apache.kafka.tools.ProducerPerformance --topic topic_name --num-records  5000 --record-size  400 --throughput 1500000 --producer-props bootstrap.servers=localhost:9092
**expected result: **
```

```

### option 2: ###

**command: **./kafka-producer-perf-test.sh --broker-list=<host>:<port> --messages <#messages> --topic <topic_name> --message-size <message-size> --batch-size <batch-size> --compression-codec <compression-codec>
**example: **./kafka-producer-perf-test.sh --broker-list=localhost:9092 --messages 10000000 --topic topic_name --message-size 1000 --batch-size 100 --compression-codec 1
**expected result: **
```

```

## Latenz ##

**command: ** ./kafka-run-class.sh kafka.tools.EndToEndLatency <host>:<port> <topic> <#messages> <acks> <message-size>
**example: **./kafka-run-class.sh kafka.tools.EndToEndLatency localhost:9092 topic 1000 all 400 
**expected result: **
```

```



