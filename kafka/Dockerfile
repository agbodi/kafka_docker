# Kafka and Zookeper setup

FROM centos:7
MAINTAINER Ade Gbodimowo
ENV KAFKA_VERSION kafka_2.11-2.0.0

# Install Kafka, Zookeeper and other needed things
RUN yum update -y && yum install epel-release -y

RUN yum install epel-release supervisor java-1.8.0-openjdk-devel java-1.8.0-openjdk wget vim net-tools -y && \
    wget http://apache.claz.org/kafka/2.0.0/${KAFKA_VERSION}.tgz -P /opt/ && \
    tar -xvf /opt/${KAFKA_VERSION}.tgz -C /opt/ && \
    rm -rf /opt/${KAFKA_VERSION}.tgz
    

# 2181 is zookeeper, 9092 is kafka
EXPOSE 2181 9092

WORKDIR /opt/${KAFKA_VERSION}

COPY zoo.sh kafka.sh /opt/${KAFKA_VERSION}/

ADD supervisor/kafka.ini supervisor/zookeeper.ini /etc/supervisord.d/

RUN chmod 700 /opt/${KAFKA_VERSION}/*.sh

CMD ["supervisord", "-n"]
