# Docker安装

## 版本选择

docker 目前分为 Community Edition (CE) 和 Enterprise Edition (EE) 两个版本。日常学习开发考虑使用CE版本。

而 Docker Community Edition (CE) 又分为 stable 和 edge 两个版本，如果不需要最新的特性，那么 stable 是比较合适的选择。

以下安装都是选择 Docker Community Edition stable 版本， 参考docker官网的文章:

https://docs.docker.com/engine/installation/

## linux下安装

以 ubuntu 为例，参考官网资料：

https://docs.docker.com/engine/installation/linux/ubuntu/

安装步骤如下：

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

## windows下安装

TBD

