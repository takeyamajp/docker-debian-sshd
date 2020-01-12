# docker-debian-sshd
[![Docker Stars](https://img.shields.io/docker/stars/takeyamajp/debian-sshd.svg)](https://hub.docker.com/r/takeyamajp/debian-sshd/)
[![Docker Pulls](https://img.shields.io/docker/pulls/takeyamajp/debian-sshd.svg)](https://hub.docker.com/r/takeyamajp/debian-sshd/)
[![license](https://img.shields.io/github/license/takeyamajp/docker-debian-sshd.svg)](https://github.com/takeyamajp/docker-debian-sshd/blob/master/LICENSE)

## Supported tags and respective Dockerfile links  
- [`latest`, `debian10`](https://github.com/takeyamajp/docker-debian-sshd/blob/master/debian10/Dockerfile)
- [`debian9`](https://github.com/takeyamajp/docker-debian-sshd/blob/master/debian9/Dockerfile)

## Image summary
    FROM debian:buster-slim  
    MAINTAINER "Hiroki Takeyama"
    
    ENV TZ Asia/Tokyo
    
    ENV ROOT_PASSWORD root
    
    EXPOSE 22

## How to use
This container can be accessed by SSH and SFTP clients.

    docker run -d --name debian-sshd \  
           -e TZ=Asia/Tokyo \  
           -e ROOT_PASSWORD=root \  
           -p 8022:22 \  
           takeyamajp/debian-sshd

You can add extra ports and volumes as follows if you want.

    docker run -d --name debian-sshd \  
           -e TZ=Asia/Tokyo \  
           -e ROOT_PASSWORD=root \  
           -p 8022:22 \  
           -p 8080:80 \  
           -v /my/own/datadir:/var/www/html \  
           takeyamajp/debian-sshd

## Time zone
You can use any time zone such as America/Chicago that can be used in Ubuntu.  

See below for zones.  
https://www.unicode.org/cldr/charts/latest/verify/zones/en.html

## Logging
This container logs the beginning, authentication, and termination of each connection.  
Use the following command to view the logs in real time.

    docker logs -f debian-sshd
