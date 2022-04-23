---
layout: post
title:  "Docker image with PHP, Apache, and mod_rewrite"
date:   2022-04-23 19:35:00 +0100
categories: docker php apache mod_rewrite github
---

TLDR: `docker run -it -p 8080:80 -v "$PWD":/var/www/html/ martinmajlis/apache-php-rewrite:latest` to run Apache with PHP and mod_rewrite from your current folder.

## Motivation

I have my side project to [convert timestamp to date](https://timestamp.online) that I have written in PHP several years ago. Today I wanted to make some modifications there but I have no longer Apache installed. Furthermore it was always time consuming to setup everything. Therefore I have decided to use docker to make my life easier.

There is [official PHP with Apache image](https://hub.docker.com/_/php) but [mod_rewrite](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) is not enabled there. So I have decided to create derived image image with PHP, Apache, and mod rewrite enabled.

## Docker Images

Dockerfile to achieve that is really simple:

```docker
FROM php:7-apache
RUN a2enmod rewrite
CMD ["apache2-foreground"]
```

However, there is no need to create such docker file, since you can use pre-build docker images:

* DockerHub: [apache-php-rewrite](https://hub.docker.com/repository/docker/martinmajlis/apache-php-rewrite)
* GitHub: [docker-apache-php-rewrite](https://github.com/martin-majlis/docker-apache-php-rewrite/pkgs/container/docker-apache-php-rewrite)

## How To Use It

It's very simple to use those docker images. Just traverse to the folder with the project and then execute following command:

```bash
docker run -it -p 8080:80 \
	-v "$PWD":/var/www/html/ \
	martinmajlis/apache-php-rewrite:latest
```

Then you can access [http://localhost:8080](http://localhost:8080) and see your web in action. To make your development simpler, you can put something like:
```
127.0.0.1	timestamp.test
```
into your `/etc/hosts` and then you can go to [http://timestamp.test:8080](http://timestamp.test:8080).