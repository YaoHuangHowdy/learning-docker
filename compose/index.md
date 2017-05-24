# Docker Compose

Docker Compose 是一个用来定义和运行复杂应用的Docker工具。

使用Compose，你可以在一个文件中定义一个多容器应用，然后使用一条命令来启动你的应用，完成一切准备工作。

## 文档

https://docs.docker.com/compose/gettingstarted/

## 安装

安装方式参考 compose release 上的说明：

https://github.com/docker/compose/releases

执行命令如下：

```bash
sudo -i
curl -L https://github.com/docker/compose/releases/download/1.13.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
exit
```

如果发现下载速度太慢，也可以自己直接找到下载的URL，手工下载：

https://github.com/docker/compose/releases/download/1.13.0/Linux-x86_64

然后手工复制到目标路径，增加运行权限：

```bash
sudo mv docker-compose-Linux-x86_64 /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

验证安装：

```bash
docker-compose version
docker-compose version 1.13.0, build 1719ceb
docker-py version: 2.2.1
CPython version: 2.7.13
OpenSSL version: OpenSSL 1.0.1t  3 May 2016
```

## 例子

```bash
docker-compose -f kafka_single.yml up -d
docker ps
```

## 参考资料

- https://henryz.gitbooks.io/learing-docker-compose/