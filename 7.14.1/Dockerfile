FROM docker.elastic.co/elasticsearch/elasticsearch:7.14.1
LABEL maintainer="uuhnaut69"

RUN yum install gcc gcc-c++ kernel-devel make boost-devel expat-devel zlib-devel bzip2-devel openssl-devel wget java-11 maven cmake -y

RUN wget https://github.com/coccoc/coccoc-tokenizer/archive/refs/heads/master.zip && \
    unzip master.zip && \
    cd coccoc-tokenizer-master && mkdir build && cd build && \
    cmake -DBUILD_JAVA=1 .. && \
    make install && \
    cp libcoccoc_tokenizer_jni.so /usr/lib/ && \
    cd ~ && \
    rm -f master.zip && \
    rm -rf coccoc-tokenizer-master

# Copy elasticsearch analysis vietnamese from file to docker container
COPY elasticsearch-analysis-vietnamese-7.14.1.zip /usr/share/elasticsearch/

RUN cd /usr/share/elasticsearch && \
    elasticsearch-plugin install --batch file:///usr/share/elasticsearch/elasticsearch-analysis-vietnamese-7.14.1.zip && \
    elasticsearch-plugin install analysis-kuromoji && \
    elasticsearch-plugin install analysis-icu