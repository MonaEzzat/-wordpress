FROM ubuntu:14.04
RUN apt-get upgrade -y -qq
RUN apt-get update -y -qq 
RUN apt-get -y -qq  install nginx
VOLUME /var/www/app

# Adding the configuration files
RUN touch /etc/nginx/nginx.conf
RUN touch /etc/nginx/conf.d/
ADD config/nginx.conf /etc/nginx/nginx.conf
ADD config/default.conf /etc/nginx/conf.d/

# Expose the port 80
EXPOSE 80

# Run nginx
ENTRYPOINT [ "/usr/sbin/nginx" ]
