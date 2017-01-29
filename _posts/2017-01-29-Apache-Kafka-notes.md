---
layout: post
title:  "Apache Kafka notes"
date:   2017-01-29 21:49:57 +0100
categories: kafka
---
Until now I used Kafka only in combination with Logstash and with a simple Pyhton consumer. Here is what I learnt from diving a bit deeper in the documentation:

### Docker
Run Kafka on a single node with the following Docker commands:
{% highlight docker %}
sudo docker run -d --net=host --name zookeeper \
	-e ZOOKEEPER_CLIENT_PORT=2181 \
	confluentinc/cp-zookeeper
sudo docker run -d --net=host --name kafka \
	-e KAFKA_ZOOKEEPER_CONNECT=localhost:2181 \
	-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092 \
	confluentinc/cp-kafka
{% endhighlight %}
To enable remote connections to the Kafka node, replace `localhost` in the `KAFKA_ADVERTISED_LISTENERS` environment variable with the Kafka node IP address.

### key/value pair
Besided a value, each record in Kafka can also have an optional key. With the Kafka Streams API it is possible to filter on key.

### Kafka Streams
In the Kafka Streams API you can find `KStream` and `KTable`, which are dual concepts as explained in the following articles:
<https://www.confluent.io/blog/introducing-kafka-streams-stream-processing-made-simple/>
<http://docs.confluent.io/3.1.2/streams/index.html>


