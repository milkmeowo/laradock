FROM debian:latest

MAINTAINER ZeroC0D3 Team<zeroc0d3.team@gmail.com>

# Set Environment Variables
ENV DEBIAN_FRONTEND noninteractive

# If you're in China, or you need to change sources, will be set CHANGE_SOURCE to true in .env.
ARG CHANGE_SOURCE=true
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list \
;fi

# Install Dependencies
RUN apt-get update && apt-get install -y apt-utils && apt-get upgrade -y
RUN mkdir /home/site && mkdir /home/site/cache
RUN apt-get install -y varnish
RUN rm -rf /var/lib/apt/lists/*

# Setting Configurations
ENV VARNISH_CONFIG  /etc/varnish/default.vcl
ENV CACHE_SIZE      128m
ENV VARNISHD_PARAMS -p default_ttl=3600 -p default_grace=3600
ENV VARNISH_PORT    6081
ENV BACKEND_HOST    localhost
ENV BACKEND_PORT    80

ADD default.vcl /etc/varnish/default.vcl
ADD start.sh /etc/varnish/start.sh

RUN chmod +x /etc/varnish/start.sh

CMD ["/etc/varnish/start.sh"]

EXPOSE 8080
