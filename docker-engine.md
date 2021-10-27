---
layout: default
title:  Docker-Engine
date:   2021-10-26 12:57:11 +0800
description: Quick start with a few docker commands
# categories: Docker
# permalink: /:categories/:title
---

# 1. Install Docker
First, we need to install [Docker Engine](https://docs.docker.com/engine/install/ubuntu/) according to the instructions on the official website. Then, for convenience, we can do the following to avoid typing 'sudo' each time. 
```shell
cat /etc/group | grep docker
sudo groupadd docker    # if no output
sudo gpasswd -a ${USER} docker
sudo service docker restart
newgrp - docker
```
# 2. Image Command
## 2.1 search
We can search [Docker Hub](https://hub.docker.com/) to find docker images that we want. Alternatively, we can use the command 'search' to print a list of images based on arguments.
```shell
docker search image-name
docker pull image-name [:tag]      # specified version
```
## 2.2 delete
To delete images, we can use the command 'rmi'
```shell
docker rmi -f image1-id image2-id ...
docker rmi -f $(docker images -aq)     # delete all images
```
# 3. Container Command
## 3.1 pull and run
Docker container is a running instance of a docker image. Here are the basic commands.
```shell
docker pull ubuntu:18.04
docker run -it ubuntu:18.04 /bin/bash   # interaction mode
exit        # stop and exit
ctrl+p+q    # stop but still running
```
## 3.2 ps
list all of the running containers
```shell
docker ps -aq      # show all and history containers with id only
```
## 3.3 remove
remove docker container
```shell
docker rm container-id
docker rm -f $(docker ps -aq)      # force to remove all of the running containers
docker ps -aq|xargs docker rm      # another way to remove
```
## 3.4 start and stop
start and stop the container
```shell
docker start container-id
docker restart container-id
docker stop container-id
docker kill container-id   # force to stop
```
## 3.5 others
other command
```shell
docker run -d image-name    # run in background, which requires foreground process
docker logs -tf --tail num container-id
docker top container-id
docker inspectcontainer-id
```
## 3.6 exec
enter the running container
```shell
docker exec -it container-id /bin/bash
```