Kafka in Docker
This repository provides everything you need to run Kafka in Docker.

For convenience also contains a packaged proxy that can be used to get data from a legacy Kafka 7 cluster into a dockerized Kafka 8.

Why?
The main hurdle of running Kafka in Docker is that it depends on Zookeeper. Compared to other Kafka docker images, this one runs both Zookeeper and Kafka in the same container. This means:

No dependency on an external Zookeeper host, or linking to another container
Zookeeper and Kafka are configured to work together out of the box

To build the image from your current working directory, simply run
dcker build -t agbodimowo/docker_kafka .

To stand up a container from the docker hub or from your local image
docker run -it -d --name mykafka  -p 2181:2181 -p 9092:9092 agbodimowo/docker_kafka

Public Build
https://registry.hub.docker.com/u/agbodimowo/docker_kafka/

Build from Source

docker build -it agbodimowo/docker_kafka kafka/

