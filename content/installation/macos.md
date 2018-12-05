---
date: 2018-10-27T09:10:00+08:00
title: MacOS安装
weight: 212
menu:
  main:
    parent: "installation"
description : "Docker在MacOS下的安装"
---

以 MacOS Mojave 为例，版本 10.14.1，参考官网文档：

https://docs.docker.com/docker-for-mac/install/

### 版本选择

新版本的MacOs 推荐使用 `Docker for Ma `，要是是Apple Mac OS Yosemite 10.10.3 或者更高. 对于早期版本的macos建议使用 [Docker Toolbox](https://docs.docker.com/toolbox/overview/) 。

我选择按照 Docker CE for Mac，官方介绍见：

https://store.docker.com/editions/community/docker-ce-desktop-mac

### 下载

下载要求有 docker id，登录之后才能下载。

https://download.docker.com/mac/stable/Docker.dmg

### 安装步骤

1. 双击 docker.dmg 文件，然后再弹出窗口中拖动到 application 中
2. 打开 Launchpad，找到 docker ，点击
3. 弹出窗口要求登录，用 docker id 登录，然后授权安装
4. 安装完毕之后，提示 docker desktop 已经安装完成并在运行，可以使用任何喜欢的终端开始

验证一下安装，看一下版本信息：

```bash
$ docker version
Client: Docker Engine - Community
 Version:           18.09.0
 API version:       1.39
 Go version:        go1.10.4
 Git commit:        4d60db4
 Built:             Wed Nov  7 00:47:43 2018
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.0
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.4
  Git commit:       4d60db4
  Built:            Wed Nov  7 00:55:00 2018
  OS/Arch:          linux/amd64
  Experimental:     false

```

验证一下：

```bash
  sudo docker run hello-world
```

输出如下：

```bash
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
d1725b59e92d: Pull complete 
Digest: sha256:0add3ace90ecb4adbf7777e9aacf18357296e799f81cabc9fde470971e499788
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

备注：macos下运行 docker，似乎没有 linux 下 root 权限的问题。

