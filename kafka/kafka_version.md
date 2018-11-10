


# Kafka version upgrade
## Main difference between kafka 


# Details
## 2.0.0
http://kafka.apache.org/documentation.html#upgrade
1. KIP-186 increases the default offset retention time from 1 day to 7 days. This makes it less likely to "lose" offsets in an application that commits infrequently. It also increases the active set of offsets and therefore can increase memory usage on the broker. Note that the console consumer currently enables offset commit by default and can be the source of a large number of offsets which this change will now preserve for 7 days instead of 1. You can preserve the existing behavior by setting the broker config offsets.retention.minutes to 1440.
2. Support for Java 7 has been dropped, Java 8 is now the minimum version required.
3. The default value for ssl.endpoint.identification.algorithm was changed to https, which performs hostname verification (man-in-the-middle attacks are possible otherwise). Set ssl.endpoint.identification.algorithm to an empty string to restore the previous behaviour.
4. KAFKA-5674 extends the lower interval of max.connections.per.ip minimum to zero and therefore allows IP-based filtering of inbound connections.
5. KIP-272 added API version tag to the metric. This will impact JMX monitoring tools that do not automatically aggregate. To get the total count for a specific request type, the tool needs to be updated to aggregate across different versions.
6. KIP-225 changed the metric "records.lag" to use tags for topic and partition. The original version with the name format "{topic}-{partition}.records-lag" has been removed.
7. The deprecated kafka.tools.ProducerPerformance has been removed, please use org.apache.kafka.tools.ProducerPerformance.
8. KIP-176 removes the --new-consumer option for all consumer based tools. This option is redundant since the new consumer is automatically used if --bootstrap-server is defined.
9. KIP-266 adds a new consumer configuration default.api.timeout.ms to specify the default timeout to use for KafkaConsumer APIs that could block. The KIP also adds overloads for such blocking APIs to support specifying a specific timeout to use for each of them instead of using the default timeout set by default.api.timeout.ms. In particular, a new poll(Duration) API has been added which does not block for dynamic partition assignment. The old poll(long) API has been deprecated and will be removed in a future version.
10. Also as part of KIP-266, the default value of request.timeout.ms has been changed to 30 seconds. The previous value was a little higher than 5 minutes to account for maximum time that a rebalance would take. Now we treat the JoinGroup request in the rebalance as a special case and use a value derived from max.poll.interval.ms for the request timeout. All other request types use the timeout defined by request.timeout.ms
11. KIP-283 improves message down-conversion handling on Kafka broker, which has typically been a memory-intensive operation. The KIP adds a mechanism by which the operation becomes less memory intensive by down-converting chunks of partition data at a time which helps put an upper bound on memory consumption. With this improvement, there is a change in FetchResponse protocol behavior where the broker could send an oversized message batch towards the end of the response with an invalid offset. Such oversized messages must be ignored by consumer clients, as is done by KafkaConsumer.  
KIP-283 also adds new topic and broker configurations message.downconversion.enable and log.message.downconversion.enable respectively to control whether down-conversion is enabled. When disabled, broker does not perform any down-conversion and instead sends an UNSUPPORTED_VERSION error to the client.    
12. Dynamic broker configuration options can be stored in ZooKeeper using kafka-configs.sh before brokers are started. This option can be used to avoid storing clear passwords in server.properties as all password configs may be stored encrypted in ZooKeeper.
13. ZooKeeper hosts are now re-resolved if connection attempt fails. But if your ZooKeeper host names resolve to multiple addresses and some of them are not reachable, then you may need to increase the connection timeout zookeeper.connection.timeout.ms.

## 1.1.0
#### Notable changes in 1.1.0
1. The kafka artifact in Maven no longer depends on log4j or slf4j-log4j12. Similarly to the kafka-clients artifact, users can now choose the logging back-end by including the appropriate slf4j module (slf4j-log4j12, logback, etc.). The release tarball still includes log4j and slf4j-log4j12.
2. KIP-225 changed the metric "records.lag" to use tags for topic and partition. The original version with the name format "{topic}-{partition}.records-lag" is deprecated and will be removed in 2.0.0.

## 1.0.*
http://kafka.apache.org/documentation.html#upgrade_100_notable
### Notable changes in 1.0.2
- It's about kafka streams. New Kafka Streams configuration parameter upgrade.from added that allows rolling bounce upgrade from version 0.10.0.x

### Notable changes in 1.0.1
- Restored binary compatibility of AdminClient's Options classes (e.g. CreateTopicsOptions, DeleteTopicsOptions, etc.) with 0.11.0.x. Binary (but not source) compatibility had been broken inadvertently in 1.0.0.
  
#### Notable changes in 1.0.0
1. Topic deletion is now enabled by default, since the functionality is now stable.   
2. If the inter.broker.protocol.version is 1.0 or later, a broker will now stay online to serve replicas on live log directories even if there are offline log directories.   
3. The overridden **handleError** method implementations have been removed from the following deprecated classes in the kafka.api package: FetchRequest, GroupCoordinatorRequest, OffsetCommitRequest, OffsetFetchRequest, OffsetRequest, ProducerRequest, and TopicMetadataRequest. This was only intended for use on the broker, but it is no longer in use and the implementations have not been maintained. A stub implementation has been retained for binary compatibility.  
4. config/consumer.properties file updated to use new consumer config properties.  
5. Kafka metrics may now contain non-numeric values.
6. Every Kafka rate metric now has a corresponding cumulative count metric with the suffix -total to simplify downstream processing. For example, records-consumed-rate has a corresponding metric named records-consumed-total.

## 0.10.1.0



### 0.10.*
http://kafka.apache.org/documentation.html#upgrade_10
#### Notable changes in 0.10.1.0 
1. The new Java consumer is no longer in beta and we recommend it for all new development.  
2. The new Java Consumer now supports heartbeating from a background thread.  

#### Notable changes in 0.10.0.0 from 0.80
1. Kafka Streams added.
2. Producer change: The old Scala producer has been deprecated. Users should migrate their code to the Java producer included in the kafka-clients JAR as soon as possible.
3. The new consumer API has been marked stable.
4. Some parameters change.