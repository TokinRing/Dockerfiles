FROM tokinring/alpine
MAINTAINER TokinRing [support@gnetsolutions.net]

RUN apk --no-cache add libressl mariadb mariadb-client nginx supervisor php7-fpm php7-mysqli php7-pdo_mysql tzdata && mkdir /www && printf "<? phpinfo(); ?>" > /www/index.php && cp /usr/share/zoneinfo/America/Los_Angeles /etc/localtime && printf "America/Los_Angeles" > /etc/timezone && mkdir /run/mysqld && chown mysql /run/mysqld

RUN export DATABASE_PASS="SuperSecretPassword" && su mysql -s /bin/sh -c "mysql_install_db --user=mysql --datadir=/var/lib/mysql" && su mysql -s /bin/sh -c "mysqld &" && sleep 10 && mysqladmin -u root password "$DATABASE_PASS" && mysql -u root -p"$DATABASE_PASS" -e "UPDATE mysql.user SET Password=PASSWORD('$DATABASE_PASS') WHERE User='root'" && mysql -u root -p"$DATABASE_PASS" -e "DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost', '127.0.0.1', '::1')" && mysql -u root -p"$DATABASE_PASS" -e "DELETE FROM mysql.user WHERE User=''" && mysql -u root -p"$DATABASE_PASS" -e "DELETE FROM mysql.db WHERE Db='test' OR Db='test\_%'" && mysql -u root -p"$DATABASE_PASS" -e "FLUSH PRIVILEGES" && mysqld stop

EXPOSE 80

COPY ./config/supervisord.conf /etc/
COPY ./config/dhparam.pem /etc/ssl/
COPY ./config/nginx.conf /etc/nginx/
COPY ./config/nginx-default.conf /etc/nginx/conf.d/
COPY ./config/my.cnf /etc/mysql/

CMD ["supervisord", "-c", "/etc/supervisord.conf"]
