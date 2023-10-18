## Introduction
Apache Kafka is an open-source distributed streaming system used for handling the flow of large volumes of data.
Kafka has three primary capabilities:
It enables applications to publish or subscribe to data or event streams.
It stores records accurately (i.e., in the order in which they occurred) in a reliable way.
It processes records in real-time (as they occur).

## Architecture

### Producer
The producer is an application that sends data or messages. The message may have different meanings to us, but for Kafka, it is a simple array of bytes.
For example, if we need to send a text file to Kafka, we can create a producer application and send each line as a message.
In this case, the message is text, but for Kafka, it's just an array of bytes. So while working with Kafka, if you want to send some data,
You have to create a producer application; it is very unlikely that you will get an already-made producer that fits your purpose.

### Consumer
The consumer is again an application that receives data. If producers are sending data, they must be sending it to someone.
The consumers are the recipients, but the producers don't send data to a recipient address; they just send it to the Kafka server, and anyone who is interested in that data can come forward and take it from the Kafka server.
So an application that requests data from a Kafka server is a consumer, and they can request data sent by any producer, provided they have permission to read it.
So just continuing on the file example, if you want to read the file sent by a producer, you have to create a consumer application.
then it will request Kafka for the data. The Kafka server will send me some messages.
In this example, the client application will receive some lines from the Kafka server.
It will process them and again request some more messages. The client keeps requesting data from Kafka, and Kafka will keep giving message records as long as new messages are coming from the producer.

### Broker
The broker is a Kafka server. It's just a meaningful name given to the Kafka server.
All that Kafka does is act as a message broker between producer and consumer. The producer and consumer don't interact directly.
They use the Kafka server as an agent and a broker to exchange messages.
A Kafka cluster consists of multiple brokers. It simply means a group of computers, each executing one instance of the Kafka broker.

## Key Concepts

### Topic
We need to have some identification mechanism to identify which consumers need which message.
The topic is an arbitrary name given to a data set. It is a unique name for a data stream.

### Partitions
The data can be hewed. It may be larger than the storage capacity of a single computer. In that case, the broker may have a challenge storing that data.
One obvious solution is to break it into two or more parts and distribute them to multiple computers.
Kafka is a distributed system that runs on a cluster of computers, so it is very obvious that Kafka can break a topic into partitions and store one partition on one computer, and that's what the partition means.
You may be wondering how Kafka will decide on the number of partitions.
The answer is simple. Kafka doesn't take that decision. We have to make that decision when we create a topic. We will take that decision, and Kafka Broker will create that many partitions for your topic.

## Offsets
It is a sequence number of a message in a partition. 
This number is assigned as the message arrives in the partition and these numbers once assigned, they never change. 
They are immutable. This sequencing means that Kafka stores messages in the order of arrival within a partition.
The first message gets an offset 0, the next message gets an offset one, and so on There is no global offset across partitions. 
Offsets are local to the partition, so if you want to locate a message you should know 3 things, topic name, partition number and offset number. 

## Replication
Kafka replicates data for fault tolerance. 
Each partition can have multiple replicas, and one of them is the leader, which serves read and write requests while other replicas replicate the data.
![1_0QqLTumYuNrpmNoZr1QoEA](https://github.com/SeenaChristin/LifeSkills/assets/120023613/2ec2438e-404c-4d5c-8a05-84c55169c8dd)

### Use Cases
* Messaging
* Website Activity Tracking
* Log Aggregation
* Stream Processing
* Event Sourcing

### Conclusion
Apache Kafka is like a superstar mail carrier for computers. 
It makes sure data and messages move around system smoothly and quickly. 
With Kafka, companies can work with real-time data, keep important records, and process information as it flows, making their computer systems more efficient and reliable.

### References
1. https://kafka.apache.org/documentation/
2. https://www.youtube.com/watch?v=udnX21__SuU
3. https://www.tutorialspoint.com/apache_kafka/apache_kafka_introduction.html
4. https://medium.com/analytics-vidhya/apache-kafka-architecture-getting-started-with-apache-kafka-771d69ac6cef
