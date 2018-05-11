FROM hhvm/hhvm

LABEL maintainer="Mahmoud Zalt <mahmoud@zalt.me>"


RUN mkdir -p /var/www

COPY server.ini /etc/hhvm/server.ini

RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD ["hhvm", "-m", "server", "-c", "/etc/hhvm/server.ini"]

EXPOSE 9000
