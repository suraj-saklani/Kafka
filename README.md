# Kafka Quick Start with Docker

This repository provides a simple setup to run Kafka locally using Docker Compose and test producers and consumers.

---

## Prerequisites

- Docker installed

---

## Start Kafka

Run the following command from the root of the repository:

```bash
docker-compose -f kafka-compose.yml up -d
```

---

## Access Kafka Container

```bash
docker exec -it kafka bash
```

---

## Go to Kafka binaries

```bash
cd /opt/kafka/bin
```

---

## Create Topic

```bash
./kafka-topics.sh --create --topic orders --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
```

## Start Producer

Message with keyseprator as ":" 

```bash
./kafka-console-producer.sh --topic orders --bootstrap-server localhost:9092 --property "parse.key=true" --property "key.separator=:"
```

Type message which we want to send to topic for example: 

order1:created

order2:processed

## Start Consumer

In new terminal

```bash
docker exec -it kafka bash
```

```bash
cd /opt/kafka/bin
```

```bash
./kafka-console-consumer.sh --topic orders --bootstrap-server localhost:9092 --from-beginning --property print.partition=true --property print.offset=true --property print.key=true
```
