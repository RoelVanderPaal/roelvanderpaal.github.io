---
layout: post
title:  "Apache Kafka notes"
date:   2017-01-29 21:49:57 +0100
categories: kafka
---
### Docker
Run Kafka on a single node with the following Docker commands:

{% highlight ruby %}
sudo docker run -d --net=host --name zookeeper \
	-e ZOOKEEPER_CLIENT_PORT=2181 \
	confluentinc/cp-zookeeper
sudo docker run -d --net=host --name kafka \
	-e KAFKA_ZOOKEEPER_CONNECT=localhost:2181 \
	-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092 \
	confluentinc/cp-kafka
{% endhighlight %}

To enable remote connections to the Kafka node, replace `localhost` in the `KAFKA_ADVERTISED_LISTENERS` environment variable with the Kafka node IP address.