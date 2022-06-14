### Helm chart for Kafdrop

Helm chart to deploy Kafdrop on OpenShift (tested with 4.x).
Supports unauthenticated and SASL/PLAIN authentication.

To install:

* Create a file called values.yaml with the following content:
  ```
  kafka:
    bootstrapServer: <Kafka bootstrap server>
    securityProtocol: <Kafka security protocol - leave blank if no authentication>
    saslMechanism: <Kafka SASL mechanism - leave blank if no authentication>
    userId: <Kafka user Id>
    password: <Kafka user password>
  ```
  For example, for OpenShift Streams for Apache kafka:
  ```
  kafka:
    bootstrapServer: xxxxxx-xxxx-xx-xxxxx.bf2.kafka.rhcloud.com:443
    securityProtocol: SASL
    saslMechanism: PLAIN
    userId: srvc-acct-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    password: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
  ```
* Install the Helm Chart
  ```
  helm -f values.yaml kafdrop kafdrop/
  ```