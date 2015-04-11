############# docker datacontainer
docker create -v /data --name datacontainer busybox

############# docker php5-fpm
docker build --tag=kim-php5.6-fpm kim-php5.6-fpm
docker run -d --volumes-from datacontainer --name kim-php5.6-fpm kim-php5.6-fpm

############# docker apache
docker build --tag=kim-apache2.2 apache2.2
docker run -d --volumes-from datacontainer -p 80:80 --link kim-php5.6-fpm:php5-fpm --name kim-apache2.2 kim-apache222

############# docker php5-cli
docker build --tag=kim-php5.6-cli kim-php5.6-cli
docker run -it --rm --volumes-from datacontainer kim-php5.6-cli /bin/bash

