FROM hhvm/hhvm

MAINTAINER Mahmoud Zalt <mahmoud@zalt.me>


RUN mkdir -p /var/www

ADD server.ini /etc/hhvm/server.ini

RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD ["hhvm", "-m", "server", "-c", "/etc/hhvm/server.ini"]

EXPOSE 9000
