# Quotas for Kafka


### Introduction:
Quotas regulate the traffic volume of clients. Quotas define the limit of throughput.  

### Motivation:
To pretend that clients monopolize broker resources and slow down other clients. High traffic can cause to a DoS behaviour.

### Order of Quotas
smaller number hits higher number.<br>
The order of precedence for quota configuration is:<br>
Stored in Zookeeper under: 										# Means: <br>
1./config/users/<user>/clients/<client-id> 		# Combination of user and client ID <br>
2./config/users/<user>/clients/<default>	 		# ? <br>
3./config/users/<user>										 		# Only User quota <br>
4./config/users/<default>/clients/<client-id> # <br>
5./config/users/<default>/clients/<default>   # ? <br>
6./config/users/<default>											# User default quota <br>
7./config/clients/<client-id>									# Only ClientID <br>
8./config/clients/<default>										# ? Client ID default <br>



More details: <br>
[quotas](http://kafka.apache.org/documentation.html#quotas)
[design-quotas](http://kafka.apache.org/documentation.html#design_quotas)
[KIP-55](https://cwiki.apache.org/confluence/display/KAFKA/KIP-55%3A+Secure+Quotas+for+Authenticated+Users)

### Setting Quotas Kafka

#### Set default quotas:
To set for all clients or users default quotas. <br>
**command:** kafka-configs --zookeeper localhost:2181 --alter --add-config 'producer_byte_rate=1024, consumer_byte_rate=2048' --entity-type {entity-type} --entity-default<br>
**example:** kafka-configs --zookeeper localhost:2181 --alter --add-config 'producer_byte_rate=1024, consumer_byte_rate=2048' --entity-type clients --entity-default<br>

**options:** <br>
For user add:     *--entity-type users* <br>
For clients add:  *--entity-type clients* <br>


##### Custom Quotas:



  **command:** kafka-configs --zookeeper localhost:2181 --alter --add-config 'producer_byte_rate={  }, consumer_byte_rate={  } --entity-type users --entity-name {username} --entity-type clients --entity-name {username}<br>
  **example:** <br>
  ```
  Created topic "topic_name".
  ```

#### List and describe Quotas
  **command:** kafka-configs.sh --zookeeper localhost:2181 --describe<br>
  **example:** <br>
  ```
TODO
  ```
  **options:** <br>
  Use entity-type **users** to list all or a specific user <br>
  *--entity-type users*		 			 
  *--entity-name {specific_user_name} #Optional*

  Use entity-type clients to list all or a specific client <br>
  *--entity-type clients*
  *--entity-name specific_client_id #Optional*
