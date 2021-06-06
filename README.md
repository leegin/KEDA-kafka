# KEDA-kafka

The application consists of two components.

kafka-producer — this component will produce messages (Order messages to be precise) to the Kafka topic we created. The number of messages to be pushed can be provided through a REST endpoint.

kafka-consumer — this component will consume messages from the Kafka topic and mark the Order status to SHIPPED . Ideally this is the component that should scale depending on the number of messages in the queue.

To build the everything in one go execute the below command in the terminal. This will compile the source and also package the Vertx services in to “fat” jars, which we will use to build the docker images.

```mvn clean install```
