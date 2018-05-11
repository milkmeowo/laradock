FROM python:slim

LABEL maintainer="melchabcede@gmail.com"

# If you're in China, or you need to change sources, will be set CHANGE_SOURCE to true in .env.
ARG CHANGE_SOURCE=true
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list \
;fi


RUN pip install --upgrade --no-cache-dir awsebcli
RUN apt-get -yqq update && apt-get -yqq install git-all

#NOTE: make sure ssh keys are added to ssh_keys folder

RUN mkdir root/tmp_ssh
COPY /ssh_keys/. /root/.ssh/
RUN cd /root/.ssh && chmod 600 * && chmod 644 *.pub

# Set default work directory
WORKDIR /var/www


