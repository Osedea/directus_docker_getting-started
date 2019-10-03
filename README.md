# Getting started with Directus 7 And Docker (Nginx, PHP & MySQL)

Read the Medium blog post: https://medium.com/@Adrien0/getting-started-with-directus-7-and-docker-nginx-php-mysql-caa9f4351bcb

## What the hell is that?

A repository containing a few files to help you getting started in no time with [Directus](https://directus.io) and [Docker](http://docker.com) !

## Docker commands

### Start stuff

```
docker build -t directus_img .
docker network create directus_test_network
docker run -dit --name directus_php --network directus_test_network -p 8000:80 -v "$(pwd)/directus/":/app/ --rm directus_img
docker run -d --name directus_mysql --network directus_test_network -p 3306:3306 -e MYSQL_DATABASE=directus -e MYSQL_ROOT_PASSWORD=root -v data:"$(pwd)/data" --rm mysql:5.7
```

### Stop stuff

```
docker stop directus_php
docker stop directus_mysql
```

### Restart stuff that are stopped

```
docker start directus_php
docker start directus_mysql
```

### Delete stuff

```
docker rm --force directus_php
docker rm --force directus_mysql
docker network rm directus_test_network
docker rmi directus_img
```

