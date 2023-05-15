FROM ubuntu:latest

ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update
RUN apt-get install nginx php8.1-fpm supervisor -y && rm -rf /var/lib/apt/lists/*

ENV nginx_vhost /etc/nginx/sites-available/default
ENV php_conf /etc/php/8.1/fpm/php.ini
ENV nginx_conf /etc/nginx/nginx.conf
ENV supervisor_conf /etc/supervisor/supervisord.conf

COPY default ${nginx_vhost}
RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' ${php_conf} && echo "\ndaemon off;" >> ${nginx_conf}

COPY supervisord.conf ${supervisor_conf}

RUN mkdir -p /run/php && chown -R www-data:www-data /var/www/html && chown -R www-data:www-data /run/php

VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

COPY start.sh /start.sh
CMD ["./start.sh"]

EXPOSE 80 443
