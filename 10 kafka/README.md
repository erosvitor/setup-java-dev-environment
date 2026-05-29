
## About
Preparing Kafka environment.

## Steps 

### Dockerfile
Create file named kafka.yaml
```
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    container_name: zookeeper
    networks: 
      - broker-kafka
    ports:
      - 2181:2181
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000
  kafka:
    depends_on:
      - zookeeper
    image: confluentinc/cp-kafka:latest
    container_name: kafka
    networks: 
      - broker-kafka
    ports:
      - 9092:9092
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://kafka:29092,PLAINTEXT_HOST://localhost:9092
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT
      KAFKA_INTER_BROKER_LISTENER_NAME: PLAINTEXT
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
  kafdrop:
    depends_on:
      - kafka
    image: obsidiandynamics/kafdrop:latest
    container_name: kafdrop
    networks: 
      - broker-kafka
    ports:
      - 19000:9000
    environment:
      KAFKA_BROKERCONNECT: kafka:29092

networks: 
  broker-kafka:
    driver: bridge
    name: kafka
```
### Container
Create container
```
docker compose -f kafka.yaml up -d
```

### Testing

Create topic
```
$ kafka-topics --create --topic helloworld --bootstrap-server localhost:9092
```

List topics
```
$ kafka-topics --list --bootstrap-server localhost:9092
```

Details from topic
```
$ kafka-topics --describe --topic helloworld --bootstrap-server localhost:9092
```

Produce message
```
$ kafka-console-producer --topic helloworld --bootstrap-server localhost:9092
```

Consume message
```
$ kafka-console-consumer --topic helloworld --from-beginning --bootstrap-server localhost:9092
```
