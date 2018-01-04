# Install

## Ubuntu 14.04
sudo apt-get install cgroup-lite

## Configuration
vim /etc/docker/daemon.json
{
  "registry-mirrors": ["https://oj6hoh2j.mirror.aliyuncs.com"]
}

## Run
sudo docker run -it python:2.7 /bin/bash
sudo docker ps -a
sudo docker start HASH 
sudo docker exec -it HASH /bin/bash



