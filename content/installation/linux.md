---
date: 2018-10-27T09:10:00+08:00
title: Linux安装
weight: 210
menu:
  main:
    parent: "installation"
description : "Docker在Linux下的安装"
---

以 ubuntu 为例，参考官网文档：

https://docs.docker.com/install/linux/docker-ce/ubuntu/

## 安装准备

看一下自己的Linux机器版本和内核信息：

- `uname --all`

	```bash
	Linux skyserver 4.4.0-92-generic #115-Ubuntu SMP Thu Aug 10 09:04:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
	```

- `cat /proc/version`

	```bash
	Linux version 4.4.0-92-generic (buildd@lcy01-17) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #115-Ubuntu SMP Thu Aug 10 09:04:33 UTC 2017
	```

- `lsb_release -a`

	```bash
    No LSB modules are available.
    Distributor ID:	LinuxMint
    Description:	Linux Mint 18.1 Serena
    Release:	18.1
    Codename:	serena
	```

## 安装步骤

1. 卸载旧版本

	```bash
	  sudo apt-get remove docker docker-engine
	```

2. 安装docker

	简单起见，使用 docker 仓库安装。

	```bash
	  sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
	  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
	  sudo apt-get update
	  sudo apt-get install docker-ce
	```

3. 验证安装

	安装完成之后，验证一下：

	```bash
	  sudo docker run hello-world
	```

	输出如下：

	```bash
	  $ sudo docker run hello-world
	  Unable to find image 'hello-world:latest' locally
	
	  latest: Pulling from library/hello-world
	  78445dd45222: Pull complete
	  Digest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7
	  Status: Downloaded newer image for hello-world:latest
	
	  Hello from Docker!
	  This message shows that your installation appears to be working correctly.
	  ...
	```

4. 设置权限避免每次sudo

	为了以非root用户使用docker, 可以将用户加入"docker"组.

	```bash
	  sudo usermod -aG docker sky
	```

	重新登录之后生效。