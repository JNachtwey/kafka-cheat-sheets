## Authorization with Access Control Lists ##

Summary for ACLs based on [Apache Kafka Docu](https://kafka.apache.org/documentation/#security_authz)
To activate ACLS set in server.properties:
'''
allow.everyone.if.no.acl.found=false
'''
If this value is on true, only the topics on which are ACLs are set are secured.

After ACL activation only authenticated and authorized user and also the super users have access.
The *super user* is set in server.properties:
'''super.users=User:kafka'''

*Principal* is [Allowed/Denied] *Operation* From *Host* On *Resource*

*Principal:*
	SSL: "CN=value,OU=value,O=value,L=value,ST=value,C=value"
	Kerberos: kerberos principal name
*Operation:*
	READ
	WRITE
  DESCRIBE
	CREATE
*Host*
	IP based
*Resource:*
	Topic, Cluster


[More Details](https://kafka.apache.org/documentation/#security_authz_cli)

*Recommendation:* Set ACls for Topics to allow on Principal base the Operations.

### Basic ACL Commands ###

#### List active ACLS ####
bin/kafka-acls --authorizer-properties zookeeper.connect=localhost:2181 --list --topic test-topic

#### Adding Consumer or Producer ####
use: --producer or --consumer

example:kafka-acls --authorizer-properties zookeeper.connect=localhost:2181 --add --allow-principal User:jnachtwey *--producer* --topic mytopic
output:
Adding ACLs for resource `Topic:mytopic`:
        User:jnachtwey has Allow permission for operations: Write from hosts: *
        User:jnachtwey has Allow permission for operations: Describe from hosts: *

Adding ACLs for resource `Cluster:kafka-cluster`:
        User:jnachtwey has Allow permission for operations: Create from hosts: *

Current ACLs for resource `Topic:mytopic`:
        User:jnachtwey has Allow permission for operations: Write from hosts: *
        User:jnachtwey has Allow permission for operations: Describe from hosts: *


Disadvantage: Producer comes with CREATE rights. (Could create Topics) //TODO hebelt das autocreation aus?
Take Care: --produce will have "Create Rights". Better is to use not Con

#### Adding selected Rights ####



example:kafka-acls --authorizer-properties zookeeper.connect=localhost:2181 --add --allow-principal User:jnachtwey *--producer* --topic mytopic
output:
Adding ACLs for resource `Topic:mytopic`:
        User:jnachtwey has Allow permission for operations: Write from hosts: *
        User:jnachtwey has Allow permission for operations: Describe from hosts: *

Adding ACLs for resource `Cluster:kafka-cluster`:
        User:jnachtwey has Allow permission for operations: Create from hosts: *

Current ACLs for resource `Topic:mytopic`:
        User:jnachtwey has Allow permission for operations: Write from hosts: *
        User:jnachtwey has Allow permission for operations: Describe from hosts: *
#### Remove ####
use: --remove

example: kafka-acls --authorizer-properties zookeeper.connect=localhost:2181 --add --allow-principal User:jnachtwey --producer --topic mytopic


Authorizer Logging:
To enable the authorizer logs it is neccessay to set logging level for to *DEBUG*.
*log4j.properties:*

'''
log4j.logger.kafka.authorizer.logger=*DEBUG*, authorizerAppender
log4j.additivity.kafka.authorizer.logger=*true*
'''
