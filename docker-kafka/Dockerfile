FROM openjdk:8-jre-alpine

ENV KAFKA_VERSION="2.7.0"
ENV KAFKA_HOME=/opt/kafka
ENV PATH=${PATH}:${KAFKA_HOME}/bin

RUN apk update && \
    apk add bash && \
    rm -rf /var/cache/apk/*

ADD https://downloads.apache.org/kafka/${KAFKA_VERSION}/kafka_2.13-${KAFKA_VERSION}.tgz /tmp

RUN mkdir -p /opt && \
    tar -xvzf /tmp/kafka_2.13-${KAFKA_VERSION}.tgz -C /opt && \
    rm /tmp/kafka_2.13-${KAFKA_VERSION}.tgz && \
    mv /opt/kafka_2.13-${KAFKA_VERSION} ${KAFKA_HOME}

WORKDIR ${KAFKA_HOME}

CMD ["bin/kafka-server-start.sh", "config/server.properties"]
