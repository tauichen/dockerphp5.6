FROM php:5.6-fpm

RUN echo "deb http://packages.dotdeb.org wheezy-php56 all" >> /etc/apt/sources.list.d/dotdeb.list && \
    echo "deb-src http://packages.dotdeb.org wheezy-php56 all" >> /etc/apt/sources.list.d/dotdeb.list && \
    echo "deb http://packages.dotdeb.org wheezy all" >> /etc/apt/sources.list.d/dotdeb.list 

ADD ./dotdeb.gpg /docker/

RUN export TERM=linux && \
    apt-key add /docker/dotdeb.gpg && \
    apt-get update && \
    apt-get install -y php5-fpm php5-cgi php5-cli php5-curl php5-gd php5-mcrypt php5-mysql php5-memcache php5-xmlrpc php5-memcached && \
    apt-get install -y supervisor 

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN sed -i -e 's/listen = \/var\/run\/php5-fpm.sock/listen = 0.0.0.0:9000/g' /etc/php5/fpm/pool.d/www.conf && \
    sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php5/fpm/php-fpm.conf

WORKDIR /var/app

EXPOSE 9000

CMD ["/usr/bin/supervisord"]
