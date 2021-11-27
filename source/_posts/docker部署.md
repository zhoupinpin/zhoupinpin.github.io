---
title: docker部署
date: 2021-11-27 12:28:11
tags:
    - 技术
---
## 安装
服务器版本:CentOS 8.2 64位
```
# 1、安装yum-utils
yum install -y yum-utils

# 2、配置国内源
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

# 3、解决problem with installed package podman-1.6.4-10.的报错
yum erase podman buildah

# 4、安装Docker
yum install -y docker-ce docker-ce-cli  containerd.io --nobest

# 5、查看Docker版本
# 简单信息
docker -v
# 查看docker的版本号，包括客户端、服务端、依赖的Go等
docker version
# 查看系统(docker)层面信息，包括管理的images, containers数等
docker info
```

## Docker服务相关
```
# 1、启动
systemctl start docker

#开机自启
systemctl enable docker

# 2、停止
systemctl stop docker

# 3、重启
systemctl restart docker

# 4、查看docker状态
systemctl status docker
```
