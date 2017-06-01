Options for `kafka-console-producer`:

    Read data from standard input and publish it to Kafka.
    Option                                   Description
    ------                                   -----------
    --batch-size <Integer: size>             Number of messages to send in a single
                                               batch if they are not being sent
                                               synchronously. (default: 200)
    --broker-list <String: broker-list>      REQUIRED: The broker list string in
                                               the form HOST1:PORT1,HOST2:PORT2.
    --compression-codec [String:             The compression codec: either 'none',
      compression-codec]                       'gzip', 'snappy', or 'lz4'.If
                                               specified without value, then it
                                               defaults to 'gzip'
    --key-serializer <String:                The class name of the message encoder
      encoder_class>                           implementation to use for
                                               serializing keys. (default: kafka.
                                               serializer.DefaultEncoder)
    --line-reader <String: reader_class>     The class name of the class to use for
                                               reading lines from standard in. By
                                               default each line is read as a
                                               separate message. (default: kafka.
                                               tools.
                                               ConsoleProducer$LineMessageReader)
    --max-block-ms <Long: max block on       The max time that the producer will
      send>                                    block for during a send request
                                               (default: 60000)
    --max-memory-bytes <Long: total memory   The total memory used by the producer
      in bytes>                                to buffer records waiting to be sent
                                               to the server. (default: 33554432)
    --max-partition-memory-bytes <Long:      The buffer size allocated for a
      memory in bytes per partition>           partition. When records are received
                                               which are smaller than this size the
                                               producer will attempt to
                                               optimistically group them together
                                               until this size is reached.
                                               (default: 16384)
    --message-send-max-retries <Integer>     Brokers can fail receiving the message
                                               for multiple reasons, and being
                                               unavailable transiently is just one
                                               of them. This property specifies the
                                               number of retires before the
                                               producer give up and drop this
                                               message. (default: 3)
    --metadata-expiry-ms <Long: metadata     The period of time in milliseconds
      expiration interval>                     after which we force a refresh of
                                               metadata even if we haven't seen any
                                               leadership changes. (default: 300000)
    --old-producer                           Use the old producer implementation.
    --producer-property <String:             A mechanism to pass user-defined
      producer_prop>                           properties in the form key=value to
                                               the producer.
    --producer.config <String: config file>  Producer config properties file. Note
                                               that [producer-property] takes
                                               precedence over this config.
    --property <String: prop>                A mechanism to pass user-defined
                                               properties in the form key=value to
                                               the message reader. This allows
                                               custom configuration for a user-
                                               defined message reader.
    --queue-enqueuetimeout-ms <Integer:      Timeout for event enqueue (default:
      queue enqueuetimeout ms>                 2147483647)
    --queue-size <Integer: queue_size>       If set and the producer is running in
                                               asynchronous mode, this gives the
                                               maximum amount of  messages will
                                               queue awaiting sufficient batch
                                               size. (default: 10000)
    --request-required-acks <String:         The required acks of the producer
      request required acks>                   requests (default: 1)
    --request-timeout-ms <Integer: request   The ack timeout of the producer
      timeout ms>                              requests. Value must be non-negative
                                               and non-zero (default: 1500)
    --retry-backoff-ms <Integer>             Before each retry, the producer
                                               refreshes the metadata of relevant
                                               topics. Since leader election takes
                                               a bit of time, this property
                                               specifies the amount of time that
                                               the producer waits before refreshing
                                               the metadata. (default: 100)
    --socket-buffer-size <Integer: size>     The size of the tcp RECV size.
                                               (default: 102400)
    --sync                                   If set message send requests to the
                                               brokers are synchronously, one at a
                                               time as they arrive.
    --timeout <Integer: timeout_ms>          If set and the producer is running in
                                               asynchronous mode, this gives the
                                               maximum amount of time a message
                                               will queue awaiting sufficient batch
                                               size. The value is given in ms.
                                               (default: 1000)
    --topic <String: topic>                  REQUIRED: The topic id to produce
                                               messages to.
    --value-serializer <String:              The class name of the message encoder
      encoder_class>                           implementation to use for
                                               serializing values. (default: kafka.
                                               serializer.DefaultEncoder)


Publish data to a topic:

    root@fast-data-dev / $ echo "your message" | kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic

Options for `kafka-console-consumer`:

    The console consumer is a tool that reads data from Kafka and outputs it to standard output.
    Option                                   Description
    ------                                   -----------
    --blacklist <String: blacklist>          Blacklist of topics to exclude from
                                               consumption.
    --bootstrap-server <String: server to    REQUIRED (unless old consumer is
      connect to>                              used): The server to connect to.
    --consumer-property <String:             A mechanism to pass user-defined
      consumer_prop>                           properties in the form key=value to
                                               the consumer.
    --consumer.config <String: config file>  Consumer config properties file. Note
                                               that [consumer-property] takes
                                               precedence over this config.
    --csv-reporter-enabled                   If set, the CSV metrics reporter will
                                               be enabled
    --delete-consumer-offsets                If specified, the consumer path in
                                               zookeeper is deleted when starting up
    --enable-systest-events                  Log lifecycle events of the consumer
                                               in addition to logging consumed
                                               messages. (This is specific for
                                               system tests.)
    --formatter <String: class>              The name of a class to use for
                                               formatting kafka messages for
                                               display. (default: kafka.tools.
                                               DefaultMessageFormatter)
    --from-beginning                         If the consumer does not already have
                                               an established offset to consume
                                               from, start with the earliest
                                               message present in the log rather
                                               than the latest message.
    --key-deserializer <String:
      deserializer for key>
    --max-messages <Integer: num_messages>   The maximum number of messages to
                                               consume before exiting. If not set,
                                               consumption is continual.
    --metrics-dir <String: metrics           If csv-reporter-enable is set, and
      directory>                               this parameter isset, the csv
                                               metrics will be outputed here
    --new-consumer                           Use the new consumer implementation.
                                               This is the default.
    --offset <String: consume offset>        The offset id to consume from (a non-
                                               negative number), or 'earliest'
                                               which means from beginning, or
                                               'latest' which means from end
                                               (default: latest)
    --partition <Integer: partition>         The partition to consume from.
    --property <String: prop>                The properties to initialize the
                                               message formatter.
    --skip-message-on-error                  If there is an error when processing a
                                               message, skip it instead of halt.
    --timeout-ms <Integer: timeout_ms>       If specified, exit if no message is
                                               available for consumption for the
                                               specified interval.
    --topic <String: topic>                  The topic id to consume on.
    --value-deserializer <String:
      deserializer for values>
    --whitelist <String: whitelist>          Whitelist of topics to include for
                                               consumption.
    --zookeeper <String: urls>               REQUIRED (only when using old
                                               consumer): The connection string for
                                               the zookeeper connection in the form
                                               host:port. Multiple URLS can be
                                               given to allow fail-over.


Consuming data from a topic:

    root@fast-data-dev / $ kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic --from-beginning



Consuming data from a topic using `consumer-property`:

    root@fast-data-dev / $ kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic --consumer-property group.id=testgroup --from-beginning


Java Producer Demo:


```java
import org.apache.kafka.clients.producer.Producer;
import org.apache.kafka.clients.producer.ProducerRecord;
import org.apache.kafka.common.serialization.IntegerDeserializer;
import org.apache.kafka.common.serialization.StringSerializer;

import java.util.Properties;

public class KafkaProducerDemo {
    public static void main(String[] args) {
        Properties properties = new Properties();

        // kafka bootstrap server
        properties.setProperty("bootstrap.servers", "127.0.0.1:9092");
        properties.setProperty("key.serializer", StringSerializer.class.getName());
        properties.setProperty("value.serializer", StringSerializer.class.getName());
        // producer acks
        properties.setProperty("acks", "1");
        properties.setProperty("retries", "3");
        properties.setProperty("linger.ms", "1");

        Producer<String, String> producer = new org.apache.kafka.clients.producer.KafkaProducer<String, String>(properties);


        for (int key=0; key < 10; key++){
            ProducerRecord<String, String> producerRecord =
                    new ProducerRecord<String, String>("second_topic", Integer.toString(key), "message that has key: " + Integer.toString(key));
            producer.send(producerRecord);
        }



        producer.close();
    }
}
```


Java Consumer Demo:

```java
import org.apache.kafka.clients.consumer.ConsumerRecord;
import org.apache.kafka.clients.consumer.ConsumerRecords;
import org.apache.kafka.clients.consumer.KafkaConsumer;
import org.apache.kafka.common.serialization.StringDeserializer;

import java.util.Arrays;
import java.util.Properties;

public class KafkaConsumerDemo {
    public static void main(String[] args) {
        Properties properties = new Properties();

        // kafka bootstrap server
        properties.setProperty("bootstrap.servers", "127.0.0.1:9092");
        properties.setProperty("key.deserializer", StringDeserializer.class.getName());
        properties.setProperty("value.deserializer", StringDeserializer.class.getName());

        properties.setProperty("group.id", "test");
        properties.setProperty("enable.auto.commit", "false");
//        properties.setProperty("auto.commit.interval.ms", "1000");
        properties.setProperty("auto.offset.reset", "earliest");

        KafkaConsumer<String, String> kafkaConsumer = new KafkaConsumer<String, String>(properties);
        kafkaConsumer.subscribe(Arrays.asList("second_topic"));

        while(true) {
            ConsumerRecords<String, String> consumerRecords = kafkaConsumer.poll(100);
            for (ConsumerRecord<String, String> consumerRecord : consumerRecords) {
//                consumerRecord.value();
//                consumerRecord.key();
//                consumerRecord.offset();
//                consumerRecord.partition();
//                consumerRecord.topic();
//                consumerRecord.timestamp();

                System.out.println("Partition: " + consumerRecord.partition() +
                                    ", Offset: " + consumerRecord.offset() +
                                    ", Key: " + consumerRecord.key() +
                                    ", Value: " + consumerRecord.value());

            }
            kafkaConsumer.commitSync();
        }
    }
}
```
