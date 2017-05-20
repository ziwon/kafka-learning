To get Kafka command lines tools:

    docker run --rm -it --net=host landoop/fast-data-dev bash

Query all the comands in this Kafka box:

    root@fast-data-dev / $ kafka-
    kafka-acls                        kafka-replica-verification
    kafka-avro-console-consumer       kafka-rest-run-class
    kafka-avro-console-producer       kafka-rest-start
    kafka-configs                     kafka-rest-stop
    kafka-console-consumer            kafka-rest-stop-service
    kafka-console-producer            kafka-run-class
    kafka-consumer-groups             kafka-server-start
    kafka-consumer-offset-checker     kafka-server-stop
    kafka-consumer-perf-test          kafka-simple-consumer-shell
    kafka-mirror-maker                kafka-streams-application-reset
    kafka-preferred-replica-election  kafka-topics
    kafka-producer-perf-test          kafka-verifiable-consumer
    kafka-reassign-partitions         kafka-verifiable-producer
    kafka-replay-log-producer

Options for `kafta-topics`:

	root@fast-data-dev / $ kafka-topics
	Create, delete, describe, or change a topic.
	Option                                   Description
	------                                   -----------
	--alter                                  Alter the number of partitions,
	                                           replica assignment, and/or
	                                           configuration for the topic.
	--config <String: name=value>            A topic configuration override for the
	                                           topic being created or altered.The
	                                           following is a list of valid
	                                           configurations:
	                                         	cleanup.policy
	                                         	compression.type
	                                         	delete.retention.ms
	                                         	file.delete.delay.ms
	                                         	flush.messages
	                                         	flush.ms
	                                         	follower.replication.throttled.
	                                           replicas
	                                         	index.interval.bytes
	                                         	leader.replication.throttled.replicas
	                                         	max.message.bytes
	                                         	message.format.version
	                                         	message.timestamp.difference.max.ms
	                                         	message.timestamp.type
	                                         	min.cleanable.dirty.ratio
	                                         	min.compaction.lag.ms
	                                         	min.insync.replicas
	                                         	preallocate
	                                         	retention.bytes
	                                         	retention.ms
	                                         	segment.bytes
	                                         	segment.index.bytes
	                                         	segment.jitter.ms
	                                         	segment.ms
	                                         	unclean.leader.election.enable
	                                         See the Kafka documentation for full
	                                           details on the topic configs.
	--create                                 Create a new topic.
	--delete                                 Delete a topic
	--delete-config <String: name>           A topic configuration override to be
	                                           removed for an existing topic (see
	                                           the list of configurations under the
	                                           --config option).
	--describe                               List details for the given topics.
	--disable-rack-aware                     Disable rack aware replica assignment
	--force                                  Suppress console prompts
	--help                                   Print usage information.
	--if-exists                              if set when altering or deleting
	                                           topics, the action will only execute
	                                           if the topic exists
	--if-not-exists                          if set when creating topics, the
	                                           action will only execute if the
	                                           topic does not already exist
	--list                                   List all available topics.
	--partitions <Integer: # of partitions>  The number of partitions for the topic
	                                           being created or altered (WARNING:
	                                           If partitions are increased for a
	                                           topic that has a key, the partition
	                                           logic or ordering of the messages
	                                           will be affected
	--replica-assignment <String:            A list of manual partition-to-broker
	  broker_id_for_part1_replica1 :           assignments for the topic being
	  broker_id_for_part1_replica2 ,           created or altered.
	  broker_id_for_part2_replica1 :
	  broker_id_for_part2_replica2 , ...>
	--replication-factor <Integer:           The replication factor for each
	  replication factor>                      partition in the topic being created.
	--topic <String: topic>                  The topic to be create, alter or
	                                           describe. Can also accept a regular
	                                           expression except for --create option
	--topics-with-overrides                  if set when describing topics, only
	                                           show topics that have overridden
	                                           configs
	--unavailable-partitions                 if set when describing topics, only
	                                           show partitions whose leader is not
	                                           available
	--under-replicated-partitions            if set when describing topics, only
	                                           show under replicated partitions
	--zookeeper <String: urls>               REQUIRED: The connection string for
	                                           the zookeeper connection in the form
	                                           host:port. Multiple URLS can be
	                                           given to allow fail-over.


Create a topic:

	root@fast-data-dev / $ kafka-topics --zookeeper 127.0.0.1:2181 --create --topic first_topic --partition 3 --replication-factor 1
	WARNING: Due to limitations in metric names, topics with a period ('.') or underscore ('_') could collide. To avoid issues it is best to use either, but not both.
	Created topic "first_topic".

Describe a topic:

	root@fast-data-dev / $ kafka-topics --zookeeper 127.0.0.1:2181 --describe --topic first_topic
	Topic:first_topic       PartitionCount:3        ReplicationFactor:1     Configs:
   			Topic: first_topic      Partition: 0    Leader: 0       Replicas: 0     Isr: 0
        	Topic: first_topic      Partition: 1    Leader: 0       Replicas: 0     Isr: 0
        	Topic: first_topic      Partition: 2    Leader: 0       Replicas: 0     Isr: 0

Delete a topic:

	root@fast-data-dev / kafka-topics --zookeeper 127.0.0.1:2181 --topic second_topic --delete
	Topic second_topic is marked for deletion.
	Note: This will have no impact if delete.topic.enable is not set to true.