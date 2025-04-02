# About this image

- Pull the image from takeyamajp/docker-rocky-sshd, then upgrade it to the latest version of Rocky Linux 9. 
- Installed packages: procps, procps-ng, iputils, bind-utils, net-tools, to support the following commands: ps, ping, nslookup, ifconfig, and top.


# rockylinux

Star this repository if it is useful for you.  
[![Docker Stars](https://img.shields.io/docker/stars/cuongitl/rockylinux.svg)](https://hub.docker.com/r/cuongitl/rockylinux/)
[![Docker Pulls](https://img.shields.io/docker/pulls/cuongitl/rockylinux.svg)](https://hub.docker.com/r/cuongitl/rockylinux/)
[![license](https://img.shields.io/github/license/cuongitl/docker-rockylinux.svg)](https://github.com/cuongitl/docker-rockylinux/blob/master/LICENSE)


## Supported tags and respective Dockerfile links  
- [`latest`, `rocky9`](https://github.com/cuongitl/rockylinux/blob/master/rocky9/Dockerfile)
- [`rocky8`](https://github.com/cuongitl/rockylinux/blob/master/rocky8/Dockerfile)

 ### Supported architectures: ([`more info`](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
 `amd64`, `arm64(for Raspberry Pi)`

## Image summary
    FROM rockylinux:9  
    MAINTAINER "Hiroki Takeyama"
    
    ENV TIMEZONE Asia/Tokyo
    
    ENV ROOT_PASSWORD root
    
    EXPOSE 22

## How to use
This container can be accessed by SSH and SFTP clients.

    docker run -d --name rockylinux \  
           -e TIMEZONE=Asia/Tokyo \  
           -e ROOT_PASSWORD=root \  
           -p 8022:22 \  
           cuongitl/rockylinux

You can add extra ports and volumes as follows if you want.

    docker run -d --name rockylinux \  
           -e TIMEZONE=Asia/Tokyo \  
           -e ROOT_PASSWORD=root \  
           -p 8022:22 \  
           -p 8080:80 \  
           -v /my/own/datadir:/var/www/html \  
           cuongitl/rockylinux

SCP command can be used for transferring files.

    scp -P 8022 -r /my/own/httpd.conf root@localhost:/etc/httpd/conf/httpd.conf

## Time zone
You can use any time zone such as America/Chicago that can be used in Rocky Linux.  

See below for zones.  
https://www.unicode.org/cldr/charts/latest/verify/zones/en.html

## Logging
This container logs the beginning, authentication, and termination of each connection.  
Use the following command to view the logs in real time.

    docker logs -f rockylinux
