FROM docker.elastic.co/elasticsearch/elasticsearch:7.3.1
LABEL maintainer="uuhnaut69"

# Copy elasticsearch analysis vietnamese from file to docker container
COPY elasticsearch-analysis-vietnamese-7.3.1.zip /usr/share/elasticsearch/

RUN cd /usr/share/elasticsearch && \
    elasticsearch-plugin install --batch file:///usr/share/elasticsearch/elasticsearch-analysis-vietnamese-7.3.1.zip && \
    elasticsearch-plugin install analysis-kuromoji && \
    elasticsearch-plugin install analysis-icu