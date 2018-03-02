#Using JDK Image
FROM openjdk:8

# Set Elasticsearch Version
ENV ELASTICSEARCH_VERSION 5.2.1

# Add esuser
RUN useradd -d /home/esuser -m esuser
WORKDIR /home/esuser

RUN mkdir /data

# Install Elastisearch and set User Permissions
RUN \
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-${ELASTICSEARCH_VERSION}.tar.gz && \
tar xvzf elasticsearch-${ELASTICSEARCH_VERSION}.tar.gz && \
rm -f elasticsearch-${ELASTICSEARCH_VERSION}.tar.gz && \
chown -R esuser:esuser elasticsearch-${ELASTICSEARCH_VERSION}

 # elasticsearch config
ADD elasticsearch.yml /home/esuser/elasticsearch-${ELASTICSEARCH_VERSION}/config/elasticsearch.yml
ENTRYPOINT elasticsearch-${ELASTICSEARCH_VERSION}/bin/elasticsearch