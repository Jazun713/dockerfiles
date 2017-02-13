FROM phusion/baseimage:0.9.19

CMD ["/sbin/my_init"]

RUN \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6 && \
    echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.4.list && \
    apt-get update && \
    apt-get install -y numactl && \
    apt-get install -y mongodb-org
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN apt-get update && apt-get upgrade -y -o Dpkg::Options::="--force-confold"

VOLUME /data/db /data/configdb
WORKDIR /data

EXPOSE 27017
#ENTRYPOINT [ "/usr/bin/mongod" ]
