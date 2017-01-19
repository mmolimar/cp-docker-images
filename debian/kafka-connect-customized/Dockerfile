FROM confluentinc/cp-kafka-connect-base

LABEL io.confluent.docker=true

ENV COMPONENT=kafka-connect-customized

ADD lib/kafka-connect-ftp-0.1-jar-with-dependencies.jar /etc/kafka-connect/jars/
ADD lib/ojdbc6.jar /etc/kafka-connect/jars/

RUN echo "===> Installing JDBC, Elasticsearch and Hadoop connectors ..." \
    && apt-get -qq update \
    && apt-get install -y \
        confluent-kafka-connect-jdbc=${CONFLUENT_VERSION}-${CONFLUENT_DEB_VERSION} \
        confluent-kafka-connect-hdfs=${CONFLUENT_VERSION}-${CONFLUENT_DEB_VERSION} \
        confluent-kafka-connect-elasticsearch=${CONFLUENT_VERSION}-${CONFLUENT_DEB_VERSION} \
    && echo "===> Cleaning up ..."  \
    && apt-get clean && rm -rf /tmp/* /var/lib/apt/lists/*

FROM confluentinc/cp-kafka-connect
