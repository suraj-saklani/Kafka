Step 1: Start Kafka using Docker Compose

  Make sure you are in the root of the repository where the compose file is present.
  docker-compose -f kafka-compose.yml up -d

Step 2: Access the Kafka container
  
  docker exec -it kafka bash
  
  Then go to Kafka binaries:
  cd /opt/kafka/bin

Step 3: Create a topic
  ./kafka-topics.sh --create --topic orders --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1

Step 4: Start a producer

  ./kafka-console-producer.sh --topic orders --bootstrap-server localhost:9092 --property "parse.key=true" --property "key.separator=:"

  You can send messages like:
  order1:created
  order2:processed

Step 5: Start a consumer
  ./kafka-console-consumer.sh --topic orders --bootstrap-server localhost:9092 --from-beginning --property print.partition=true --property print.offset=true --property print.key=true

This setup is useful to quickly understand how Kafka works with topics, partitions, keys, and offsets without any complex setup.

You can clone the repository, run one command, and start experimenting with Kafka locally.
