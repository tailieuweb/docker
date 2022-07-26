# Web environment with Docker
* php 5.6
* mysql 5.6
## mysql info
* username: root, password: web
## httpd info
* localhost
## phpmyadmin info
* localhost:9090
* username: root, password: web, server: h-mysql-web


https://github.com/dyarleniber/docker-php

docker-compose build app
docker-compose up -d
docker-compose ps
docker-compose exec app ls -l
docker-compose logs nginx
docker-compose pause
docker-compose unpause
docker-compose down


https://devops.tutorials24x7.com/blog/containerize-laravel-with-apache-mysql-and-mongodb-using-docker-containers