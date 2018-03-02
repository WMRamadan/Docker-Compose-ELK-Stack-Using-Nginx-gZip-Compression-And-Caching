#Using Nginx Image
FROM nginx

# Set Filebeat Version
ENV FILEBEAT_VERSION 5.2.1

# Install wget
RUN apt-get update -qq \
 && apt-get install -qqy wget \
 && apt-get clean

# Install Filebeat
RUN wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && dpkg -i filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && rm filebeat-${FILEBEAT_VERSION}-amd64.deb

# Remove nginx logs
RUN rm /var/log/nginx/access.log /var/log/nginx/error.log

# Filebeat config file
ADD filebeat.yml /etc/filebeat/filebeat.yml

# Add and run start script
ADD ./start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh
CMD [ "/usr/local/bin/start.sh" ]