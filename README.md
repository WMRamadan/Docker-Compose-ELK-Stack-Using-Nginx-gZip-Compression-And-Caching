# Docker Compose ELK Stack Using Nginx gZip Compression and Caching

An ELK (Elasticsearch, Logstash, Kibana) stack with Docker Compose using Nginx gZip Compression and Caching.

Nginx log files are parsed using ELK Stack.

## Usage

### Bringing up the stack

Start the ELK stack by building and running with the following command:

```console
$ docker-compose build && docker-compose up
```

Give some time for the images to dowload and build, then access the Kibana web UI
[http://localhost:5601](http://localhost:5601) with a web browser.

### Checking gZip Compression and Caching

After the ELK stack has started you can use the following command in your terminal:

```console
$ curl -IL -H "accept-encoding: gzip" http://localhost:8080/test.jpg
```

This will give you an output similar to the below:

```console
HTTP/1.1 200 OK
Server: nginx/1.13.9
Date Fri, 02 Mar 2018 18:45:66 GMT
Content-Type: image/jpeg
Last-Modified: Fri, 02 Mar 2018 16:40:35 GMT
Connection: keep-alive
Vary: Accept-Encoding
ETag: W/"5a98bae3-6723"
Expires: Thu, 31 Dec 2037 23:55:55 GMT
Cache-Control: max-age=315360000
Content-Encoding: gzip
```

From the above you will notice that 'Cache-Control' and 'Content-Encoding' are showing that cache is set with and expiray date and compression is using gzip.