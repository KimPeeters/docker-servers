FROM debian
MAINTAINER kim@xs3.nl

RUN apt-get update \
 && apt-get install -y php5-fpm php5-mysql php5-gd \
 && sed 's/;daemonize = yes/daemonize = no/' -i /etc/php5/fpm/php-fpm.conf \
 && rm -rf /var/lib/apt/lists/*

COPY pool.d/ /etc/php5/fpm/pool.d/
EXPOSE 9000
VOLUME ["/var/run/php5-fpm"]
CMD ["/usr/sbin/php5-fpm"]
