FROM tokinring/alpine
MAINTAINER TokinRing [support@gnetsolutions.net]

RUN printf 'http://mirror.clarkson.edu/alpine/edge/testing\n' >> /etc/apk/repositories && apk --no-cache add bash gosu libressl mariadb mariadb-client nginx php7-fpm php7-mysqli php7-pdo_mysql supervisor tzdata && cp /usr/share/zoneinfo/America/Los_Angeles /etc/localtime && printf "America/Los_Angeles" > /etc/timezone && mkdir /run/mysqld && chown mysql /run/mysqld && mkdir /run/nginx

EXPOSE 80

COPY ./config/supervisord.conf /etc/
COPY ./config/dhparam.pem /etc/ssl/
COPY ./config/nginx.conf /etc/nginx/
COPY ./config/nginx-www.conf /etc/nginx/conf.d/default.conf
COPY ./config/php-fpm.conf /etc/php7/
COPY ./config/php-fpm.d-www.conf /etc/php7/php-fpm.d/www.conf
COPY ./config/my.cnf /etc/mysql/
COPY entrypoint.sh /usr/local/bin/

#VOLUME /var/lib/mysql
#VOLUME /www

#RUN touch /var/log/supervisord.log && chown root /var/log/supervisord.log && chmod o+w /var/log/supervisord.log

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
#CMD ["supervisord", "-c", "/etc/supervisord.conf"]
