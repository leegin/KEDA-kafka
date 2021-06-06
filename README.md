# KEDA-kafka

The application consists of two components.

**Kafka-producer** — this component will produce messages (Order messages to be precise) to the Kafka topic we created. The number of messages to be pushed can be provided through a REST endpoint.

**Kafka-consumer** — this component will consume messages from the Kafka topic and mark the Order status to SHIPPED . Ideally this is the component that should scale depending on the number of messages in the queue.

To build the everything in one go execute the below command in the terminal. This will compile the source and also package the Vertx services in to “fat” jars, which we will use to build the docker images.

```mvn clean install```

If everything goes well you should see all components built successfully.

![image](https://user-images.githubusercontent.com/18220135/120936166-0ca7b680-c724-11eb-9aad-053a1c889232.png)

The next step is build the docker images. The relevant Dockerfile’s are also included in the source so it will be fairly straight forward to build the images.
Make sure that you have configured docker properly before executing below steps.

To build the producer image run the below command.

```docker build -t kafka-producer kafka-producer/```

To build the consumer image run the below command.

```docker build -t kafka-consumer kafka-consumer/```

Finally you want to push the images to a image registry like docker hub or GCR that’s accessible by your cluster.

**Credits: ChamilaLiyanage
**
