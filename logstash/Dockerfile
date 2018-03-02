#Using JDK Image
FROM openjdk:8

# Set Logstash Version
ENV LOGSTASH_VERSION 5.2.1

# Add lsuser
RUN useradd -d /home/lsuser -m lsuser
WORKDIR /home/lsuser

# Install Logstash and Set User Permissions
RUN \
wget https://artifacts.elastic.co/downloads/logstash/logstash-${LOGSTASH_VERSION}.tar.gz && \
tar xvzf logstash-${LOGSTASH_VERSION}.tar.gz && \
rm -f logstash-${LOGSTASH_VERSION}.tar.gz && \
chown -R lsuser:lsuser logstash-${LOGSTASH_VERSION}

# logstash config
ADD logstash.conf /home/lsuser
CMD logstash-${LOGSTASH_VERSION}/bin/logstash -f logstash.conf --verbose