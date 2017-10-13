### advanced Kafka security recommendations for TLS connections ###

date Oktober 2017

TLSv1.2

**server.properties**

>ssl.tls.version: TLSv1.2 </BR>
ssl.secure.random.implementation: NativePRNG </BR>
ssl.cipher.suites:


<sup>source:
https://security.stackexchange.com/questions/120347/how-to-disable-weak-cipher-suits-in-java-application-server-for-ssl
https://crypto.stackexchange.com/questions/19985/can-dh-anon-really-be-exploited-by-an-attacker
https://security.stackexchange.com/questions/145855/how-to-enforce-perfect-forward-secrecy-using-jvm-properties
</sup>

**Remark**

The TLS version and cipher are also restrictable with java.security policy. The file is usually located under:

jre/lib/security/java.security. </BR>
Adjust the jdk.tls.disabledAlgorithms property. </BR> jre/lib/security/java.security. </BR>
Adjust the jdk.tls.disabledAlgorithms property.
