FROM debian
MAINTAINER kim@xs3.nl

RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list \
 && apt-get update \
 && apt-get install -y libapache2-mod-fastcgi apache2-mpm-prefork  \
 && sed -i 's#/var/www#/data#g' /etc/apache2/sites-available/default \
 && a2enmod actions \
 && rm -rf /var/lib/apt/lists/*

COPY fastcgi.conf /etc/apache2/mods-enabled/fastcgi.conf
EXPOSE 80
CMD ["/usr/sbin/apache2ctl","-D","FOREGROUND"]
