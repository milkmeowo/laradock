FROM phusion/baseimage:latest

LABEL maintainer="Mahmoud Zalt <mahmoud@zalt.me>"

# If you're in China, or you need to change sources, will be set CHANGE_SOURCE to true in .env.
ARG CHANGE_SOURCE=true
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list; \
    sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list \
;fi

COPY run-certbot.sh /root/certbot/run-certbot.sh

RUN apt-get update
RUN apt-get install -y letsencrypt

ENTRYPOINT bash -c "bash /root/certbot/run-certbot.sh && sleep infinity"
