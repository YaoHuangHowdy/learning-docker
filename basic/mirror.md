# 设置Docker镜像

## 添加 aliyun 镜像

1. 创建docker配置文件目录

    ```bash
    sudo mkdir -p /etc/systemd/system/docker.service.d
    ```

2. 添加配置文件

    ```bash
	sudo vi /etc/systemd/system/docker.service.d/mirror.conf
    ```

3. 添加如下内容

    ```bash
    [Service]
    ExecStart=
    ExecStart=/usr/bin/docker daemon -H fd:// --registry-mirror=https://vpilhtt9.mirror.aliyuncs.com
    ```

	注意: https后面填写的是 aliyun 提供的镜像地址，需要注册用户并且申请加速器。

4. 重启

    ```bash
    sudo systemctl daemon-reload
    sudo systemctl restart docker
    ```

## 参考资料

- [使用阿里云Docker镜像加速](http://warjiang.github.io/devcat/2016/11/28/%E4%BD%BF%E7%94%A8%E9%98%BF%E9%87%8C%E4%BA%91Docker%E9%95%9C%E5%83%8F%E5%8A%A0%E9%80%9F/)