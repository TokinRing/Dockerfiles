# Linux Nginx MySQL PHP (LEMP) Stack

This image uses Alpine Linux, Nginx, PHP7, and MariaDB to have a single LEMP stack container.

To run with mysql, www, and log volumes exposing port 8000 to nginx:
```
docker run -it -v $PWD/mysql:/var/lib/mysql -v $PWD/www:/www -v $PWD/log:/var/log -e MYSQL_ROOT_PASSWORD=password -p 8000:80 tokinring/lemp-alpine-arm
```

To clean:
```
sudo rm -rf mysql/* log/nginx/* log/supervisord.log log/php7/*
```
