docker常用命令

# docker守护进程

## 配置守护进程

用-H参数调整docker守护进程监听方式,比如下面指定了端口2375

	docker -d -H tcp://0.0.0.0:2375

docker客户端连接时需要用"-H :4200"来指定,如果不想每次都用-H参数,可以设置DOCKER_HOST环境变量:

	export DOCKER_HOST="tcp://0.0.0.0:2375"

## 查看守护进程

在ubuntu中,可以通过upstart的status命令来检查docker守护进程是否正常

	status docker

正常时输出如下:

	docker start/running, process 5358

状态为"start/running",进程id为5258,用ps命令验证:

    $ ps -ef  |grep 5358
    root      5358     1  0 16:53 ?        00:00:01 /usr/bin/docker daemon

# docker

## docker info 子命令

info命令查看docker信息:

	docker info

输出如下:

    $ docker info
    Containers: 1
    Images: 4
    Storage Driver: aufs
     Root Dir: /var/lib/docker/aufs
     Backing Filesystem: extfs
     Dirs: 6
     Dirperm1 Supported: true
    Execution Driver: native-0.2
    Logging Driver: json-file
    Kernel Version: 3.16.0-38-generic
    Operating System: Ubuntu 14.04.2 LTS
    CPUs: 8
    Total Memory: 15.58 GiB
    Name: skyxps
    ID: 6UM5:3IUI:CUG6:TSLT:RHRS:2KRZ:NNSS:TWY7:OPYV:I5YP:HWQ4:SH5M


### docker ps 字命令

docker ps 字命令用于查看当前系统中容器的列表:

- docker ps 列出正在运行的容器
- docker ps -a 列出所有容器,包括已经停止的.

列出来的信息包括:

- CONTAINER ID: 容器id, 例如af2c071439b9
- IMAGE: 容器的镜像
- COMMAND: 容器的退出状态
- CREATED: 容器创建时间
- STATUS: 运行状态
- PORTS: ??
- NAMES: 容器名

    $ docker ps -a
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                    PORTS               NAMES
    af2c071439b9        ubuntu              "/bin/bash"         22 hours ago        Exited (0) 22 hours ago                       reverent_blackwell

## docker的启停

### docker run 子命令

docker run 子命令用于创建容器:

	docker run -i -t ubuntu /bin/bash

### docker start 子命令

	docker start name

启动一台名为reverent_blackwell的docker:

    $ docker start reverent_blackwell
    reverent_blackwell

### docker attach 子命令

docker attach 子命令

## docker镜像

### docker pull 子命令

docker pull命令用于下载docker镜像

	docker pull busybox
    docker pull -a busybox

增加 -a 参数之后会下载所有tag的镜像,如果不带-a也不指明tag则默认下载tag为:latest的镜像.

### docker images 子命令

docker images 子命令用于获取当前本地所有的docker镜像列表:

    $ docker images
    REPOSITORY          TAG                   IMAGE ID            CREATED             VIRTUAL SIZE
    ubuntu              latest                91e54dfb1179        3 weeks ago         188.4 MB
    busybox             ubuntu-14.04          32e97f5f5d6b        5 months ago        5.609 MB
    busybox             ubuntu-12.04          faf804f0e07b        5 months ago        5.455 MB
    busybox             buildroot-2014.02     8c2e06607696        5 months ago        2.433 MB
    busybox             latest                8c2e06607696        5 months ago        2.433 MB
    busybox             buildroot-2013.08.1   3dba22db9896        5 months ago        2.489 MB

默认只显示12位长度的16进制的IMAGE ID,如果要现实全部64位长度,需要增加--no-trunc选项:

	$ docker images --no-trunc
    REPOSITORY          TAG                   IMAGE ID                                                           CREATED             VIRTUAL SIZE
    ubuntu              latest                91e54dfb11794fad694460162bf0cb0a4fa710cfa3f60979c177d920813e267c   3 weeks ago         188.4 MB

### docker inspect 子命令

docker inspect 子命令用于查看具体镜像的信息,会对容器进行详细的检查,然后返回配置信息:

    $ docker inspect ubuntu
    [
    {
        "Id": "91e54dfb11794fad694460162bf0cb0a4fa710cfa3f60979c177d920813e267c",
        "Parent": "d74508fb6632491cea586a1fd7d748dfc5274cd6fdfedee309ecdcbc2bf5cb82",
        "Comment": "",
        "Created": "2015-08-20T20:21:15.767240511Z",
        "Container": "74bb7db8d212f77ab6d467b710451e54d2c60533f641de8c91e7ef343b88a146",
        ......
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 0,
        "VirtualSize": 188359297,
        "GraphDriver": {
            "Name": "aufs",
            "Data": null
        }
    }
    ]

使用-f 或者 --format 查看结果

### docker rm 子命令

docker rm 子命令删除不用的容器

	docker rm 

### docker search 子命令

TBD

## docker运行状态

### docker logs 字命令

docker logs 字命令用于获取容器的日志

	docker logs ubuntu
    docker logs -f ubuntu			// 类似tail -f
    docker logs --tail 10 ubuntu	// 获取日志的最后10行内容
    docker logs --tail 0 -f ubuntu	// 跟踪容器的最新日志而不必读取整个日志文件
	docker logs -f ubuntu			// -t为每条日志增加时间戳

### docker top 子命令

docker top 子命令用于查看容器内运行的进程

## 操纵docker

### docker exec 子命令

docker exec 子命令用于在容器内启动新进程:

	docker exec -d 