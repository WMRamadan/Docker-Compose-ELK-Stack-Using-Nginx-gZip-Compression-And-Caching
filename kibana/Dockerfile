#Using JDK Image
FROM openjdk:8

# Set Kibana Version
ENV KIBANA_VERSION 5.2.1

# Add kbuser
RUN useradd -d /home/kbuser -m kbuser
WORKDIR /home/kbuser

# Install Kibana and Set User Permissions
RUN \
wget https://artifacts.elastic.co/downloads/kibana/kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
tar xvzf kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
rm -f kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
chown -R kbuser:kbuser kibana-${KIBANA_VERSION}-linux-x86_64

# Kibana config
ADD kibana.yml kibana-${KIBANA_VERSION}-linux-x86_64/config/kibana.yml
ENTRYPOINT kibana-${KIBANA_VERSION}-linux-x86_64/bin/kibana