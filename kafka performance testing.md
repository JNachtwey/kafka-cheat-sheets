# Kafka performance testing #

You will find all programms in bin dir. Tested under apache kafka version 0.9. [Apache Kafka](https://kafka.apache.org/)
Variables are in brackets like {varname}


## Consumer perfomance ##

**command:** ./kafka-consumer-perf-test.sh --batch-size {batch-size} --messages {#messages} --broker-list={host}:{port} --topic topic_name --group {group_name} --new-consumer <br>
**example:** ./kafka-consumer-perf-test.sh --batch-size 1000 --messages 1000 --broker-list=localhost:9092 --topic topic_name --group group_name --new-consumer --num-fetch-threads 10<br>
**options:** 
To show stats during the test: --reporting-interval {#messages} --show-detailed-stats <br> 
**expected result:** 
```
time,  data.consumed.in.MB, MB.sec, data.consumed.in.nMsg, nMsg.sec
2016-08-28 16:43:42:870, 0,  47.6837,   39.9696,  50000,   41911.1484
2016-08-28 16:43:42:897, 0,  95.3674, 5960.4645, 100000, 6250000.0000
2016-08-28 16:43:43:045, 0, 143.0511,  322.1873, 150000,  337837.8378
2016-08-28 16:43:43:147, 0, 190.7349,  467.4874, 200000,  490196.0784
2016-08-28 16:43:43:272, 0, 238.4186,  384.5461, 250000,  403225.8065
```
**remark:** It is necessary to put messages in this topic before you can receive messages with a consumer. Take care of message-size. 

## Producer perfomance ##

### option 1: kafka.tools.ProducerPerformance (Deprecated in 0.9)###

**command:** ./kafka-run-class.sh org.apache.kafka.tools.ProducerPerformance --topic {topic_name} --num-records  {#num-records} --record-size {record-size} --throughput {testing} --producer-props bootstrap.servers={host}:{port} <br>
**example:** ./kafka-run-class.sh org.apache.kafka.tools.ProducerPerformance --topic topic_name --num-records  5000 --record-size  400 --throughput 1500000 --producer-props bootstrap.servers=localhost:9092 <br>
**expected result:**
```

```

### option 2: kafka-producer-perf-test.sh ###

**command:** ./kafka-producer-perf-test.sh --broker-list={host}:{port} --messages {#messages} --topic {topic_name} --message-size {message-size} --batch-size {batch-size} --compression-codec {compression-codec} <br>
**example:** ./kafka-producer-perf-test.sh --broker-list=localhost:9092 --messages 10000000 --topic topic_name --message-size 1000 --batch-size 100 --compression-codec 1 <br>
**expected result:**
```
			 start.time, 	 			end.time, compression, message.size, batch.size, total.data.sent.in.MB, MB.sec, total.data.sent.in.nMsg,   nMsg.sec
2016-08-30 13:43:25:926, 2016-08-30 13:43:32:259, 			1,         1000, 		100, 	             95.37, 5.0588,                  100000, 15790.3048
```


## Latency ##

**command:** ./kafka-run-class.sh kafka.tools.EndToEndLatency {host}:{port} {topic} {#messages} {acks} {message-size} <br>
**example:** ./kafka-run-class.sh kafka.tools.EndToEndLatency localhost:9092 topic_name 1000 all 400 <br> 
**expected result:**
```

```



