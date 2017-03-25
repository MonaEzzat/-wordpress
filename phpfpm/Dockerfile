FROM ubuntu:14.04
RUN apt-get update -qq && apt-get -y upgrade
RUN apt-get -y -qq install php5-fpm php5-mysql
RUN touch /etc/php5/fpm/pool.d/www.conf
RUN touch /etc/php5/fpm/php-fpm.conf
# Adding the configuration files
ADD conf/www.conf /etc/php5/fpm/pool.d/www.conf
ADD conf/php-fpm.conf /etc/php5/fpm/php-fpm.conf
ADD run.sh /run.sh
VOLUME /var/www/app
EXPOSE 9000
ENTRYPOINT [ "/bin/bash", "/run.sh"]

