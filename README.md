# FLiP-OwnTracks-MQTT

MQTT Phone App to Pulsar via MQTT

https://owntracks.org/ is a cool app you can use to send your location over HTTP or MQTT.   We will use MQTT, which is actually MoP (MQTT on Pulsar) to my Pulsar cluster.

## For a no code ingest of Location Data

![Map](https://github.com/tspannhw/FLiP-OwnTracks-MQTT/blob/main/ownmap.png?raw=true)
![Map 2](https://github.com/tspannhw/FLiP-OwnTracks-MQTT/blob/main/ownmap2.png?raw=true)

![MQTT Settings](https://github.com/tspannhw/FLiP-OwnTracks-MQTT/blob/main/ownmqtt.png?raw=true)


## Runs

````

"persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755"
root@pulsar1:/opt/demo/apache-pulsar-2.9.1# bin/pulsar-client consume "persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755" -s "owntrax" -n 0
2022-03-09T19:02:43,397-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConnectionPool - [[id: 0xe2958283, L:/127.0.0.1:37880 - R:localhost/127.0.0.1:6650]] Connected to server
2022-03-09T19:02:43,574-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - Starting Pulsar consumer status recorder with config: {"topicNames":["persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755"],"topicsPattern":null,"subscriptionName":"owntrax","subscriptionType":"Exclusive","subscriptionMode":"Durable","receiverQueueSize":1000,"acknowledgementsGroupTimeMicros":100000,"negativeAckRedeliveryDelayMicros":60000000,"maxTotalReceiverQueueSizeAcrossPartitions":50000,"consumerName":null,"ackTimeoutMillis":0,"tickDurationMillis":1000,"priorityLevel":0,"maxPendingChunkedMessage":10,"autoAckOldestChunkedMessageOnQueueFull":false,"expireTimeOfIncompleteChunkedMessageMillis":60000,"cryptoFailureAction":"FAIL","properties":{},"readCompacted":false,"subscriptionInitialPosition":"Latest","patternAutoDiscoveryPeriod":60,"regexSubscriptionMode":"PersistentOnly","deadLetterPolicy":null,"retryEnable":false,"autoUpdatePartitions":true,"autoUpdatePartitionsIntervalSeconds":60,"replicateSubscriptionState":false,"resetIncludeHead":false,"keySharedPolicy":null,"batchIndexAckEnabled":false,"ackReceiptEnabled":false,"poolMessages":true,"maxPendingChuckedMessage":10}
2022-03-09T19:02:43,605-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - Pulsar client config: {"serviceUrl":"pulsar://localhost:6650/","authPluginClassName":null,"authParams":null,"authParamMap":null,"operationTimeoutMs":30000,"lookupTimeoutMs":30000,"statsIntervalSeconds":60,"numIoThreads":1,"numListenerThreads":1,"connectionsPerBroker":1,"useTcpNoDelay":true,"useTls":false,"tlsTrustCertsFilePath":"","tlsAllowInsecureConnection":false,"tlsHostnameVerificationEnable":false,"concurrentLookupRequest":5000,"maxLookupRequest":50000,"maxLookupRedirects":20,"maxNumberOfRejectedRequestPerConnection":50,"keepAliveIntervalSeconds":30,"connectionTimeoutMs":10000,"requestTimeoutMs":60000,"initialBackoffIntervalNanos":100000000,"maxBackoffIntervalNanos":60000000000,"enableBusyWait":false,"listenerName":null,"useKeyStoreTls":false,"sslProvider":null,"tlsTrustStoreType":"JKS","tlsTrustStorePath":"","tlsTrustStorePassword":"","tlsCiphers":[],"tlsProtocols":[],"memoryLimitBytes":0,"proxyServiceUrl":null,"proxyProtocol":null,"enableTransaction":false,"socks5ProxyAddress":null,"socks5ProxyUsername":null,"socks5ProxyPassword":null}
2022-03-09T19:02:43,627-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConnectionPool - [[id: 0x2b93a0e0, L:/127.0.0.1:37882 - R:localhost/127.0.0.1:6650]] Connected to server
2022-03-09T19:02:43,627-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ClientCnx - [id: 0x2b93a0e0, L:/127.0.0.1:37882 - R:localhost/127.0.0.1:6650] Connected through proxy to target broker at 127.0.0.1:6650
2022-03-09T19:02:43,629-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerImpl - [persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755][owntrax] Subscribing to topic on cnx [id: 0x2b93a0e0, L:/127.0.0.1:37882 - R:localhost/127.0.0.1:6650], consumerId 0
2022-03-09T19:02:43,641-0500 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerImpl - [persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755][owntrax] Subscribed to topic on localhost/127.0.0.1:6650 -- consumer: 0
2022-03-09T19:02:45,645-0500 [pulsar-client-io-1-1] INFO  com.scurrilous.circe.checksum.Crc32cIntChecksum - SSE4.2 CRC32C provider initialized
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268214,"lon":-74.529126,"m":2,"p":100.879,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870566,"vac":3,"vel":0}
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268214,"lon":-74.529126,"m":2,"p":100.879,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870568,"vac":3,"vel":0}
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268214,"lon":-74.529126,"m":2,"p":100.879,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870570,"vac":3,"vel":0}
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268221,"lon":-74.529105,"m":2,"p":100.879,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870576,"vac":3,"vel":1}
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":6,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","created_at":1646870585,"lat":40.268193,"lon":-74.529146,"m":2,"p":100.881,"SSID":"FiOS-QHW9R-5G","t":"t","tid":"55","tst":1646870404,"vac":2,"vel":1}
2022-03-09T19:03:43,609-0500 [pulsar-timer-5-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - [persistent://public/default/owntracks%2Fuser%2FB692CBD1-57AF-47EE-BD04-5CB3CBC20755] [owntrax] [eb3ed] Prefetched messages: 0 --- Consume throughput received: 0.08 msgs/s --- 0.00 Mbit/s --- Ack sent rate: 0.08 ack/s --- Failed messages: 0 --- batch messages: 0 ---Failed acks: 0
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268171,"lon":-74.52908,"m":2,"p":100.886,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870634,"vac":3,"vel":0}
----- got message -----
key:[null], properties:[], content:{"_type":"location","acc":5,"alt":35,"batt":92,"bs":2,"BSSID":"48:5d:36:cd:85:6a","conn":"w","lat":40.268186,"lon":-74.529093,"m":2,"p":100.889,"SSID":"FiOS-QHW9R-5G","t":"u","tid":"55","tst":1646870653,"vac":3,"vel":0}


````


## Not Map

![Cat](https://github.com/tspannhw/FLiP-OwnTracks-MQTT/blob/main/ownmap3.jpeg?raw=true)

