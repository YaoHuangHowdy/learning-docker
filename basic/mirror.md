# 设置Docker镜像

## 添加 aliyun 镜像

1. 设置配置文件

    ```bash
    sudo vi /etc/docker/daemon.json
    ```

	增加内容如下:

    ```json
	{
      "registry-mirrors": ["https://e3wtejq8.mirror.aliyuncs.com"]
    }
    ```

	注意: https后面填写的是 aliyun 提供的镜像地址，需要注册用户并且申请加速器。

4. 重启

    ```bash
    sudo systemctl daemon-reload
    sudo systemctl restart docker
    ```

## 增加本地私库

同样修改 `/etc/docker/daemon.json` :

```json
{
  "registry-mirrors": ["https://e3wtejq8.mirror.aliyuncs.com"],
  "insecure-registries": ["192.168.31.34"]
}
```