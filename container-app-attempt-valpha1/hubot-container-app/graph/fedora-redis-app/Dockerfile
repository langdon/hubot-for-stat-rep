FROM fedora

MAINTAINER langdon, langdon@fedoraproject.org
#Modified from https://github.com/nhoag/docker-redis, Nathaniel Hoag, info@nathanielhoag.com

ENV REDIS_VERSION 2.8.18
#ENV REDIS_DIR redis-${REDIS_VERSION}
#ENV REDIS_ARCHIVE ${REDIS_DIR}.tar.gz
#ENV REDIS_URL http://download.redis.io/releases/${REDIS_ARCHIVE}
#WORKDIR /tmp

RUN yum -y update
RUN yum -y install redis

#RUN apt-get update && \
#apt-get install -y build-essential wget && \
#wget -q ${REDIS_URL} && \
#wget -q https://raw.githubusercontent.com/antirez/redis-hashes/master/README && \
#cat README | grep ${REDIS_ARCHIVE} | awk '{print $4" "$2}' | shasum -c && \
#tar xzf ${REDIS_ARCHIVE} && \
#cd ${REDIS_DIR} && \
#make && make install && \
#cp -f src/redis-sentinel /usr/local/bin && \
#mkdir -p /etc/redis && cp -f *.conf /etc/redis && \
#rm -rf /tmp/${REDIS_DIR}* /tmp/README /var/lib/apt/lists/* && \

RUN sed -i 's/^\(bind .*\)$/# \1/' /etc/redis.conf 
RUN sed -i 's/^\(daemonize .*\)$/# \1/' /etc/redis.conf
RUN sed -i 's/^\(dir .*\)$/# \1\ndir \/data/' /etc/redis.conf
RUN sed -i 's/^\(logfile .*\)$/# \1/' /etc/redis.conf

VOLUME ["/data"]

WORKDIR /data

EXPOSE 6379

CMD ["redis-server", "/etc/redis/redis.conf"]
