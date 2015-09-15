docker的安装
==========

## linux下安装

参考docker官网的文章:

[http://docs.docker.com/linux/step_one/](http://docs.docker.com/linux/step_one/)

使用docker提供的安装脚本安装:

    wget -qO- https://get.docker.com/ | sh

安装脚本输出内容:

	......
    + sudo -E sh -c docker version
    Client:
     Version:      1.8.2
     API version:  1.20
     Go version:   go1.4.2
     Git commit:   0a8c2e3
     Built:        Thu Sep 10 19:19:00 UTC 2015
     OS/Arch:      linux/amd64

    Server:
     Version:      1.8.2
     API version:  1.20
     Go version:   go1.4.2
     Git commit:   0a8c2e3
     Built:        Thu Sep 10 19:19:00 UTC 2015
     OS/Arch:      linux/amd64

    If you would like to use Docker as a non-root user, you should now consider
    adding your user to the "docker" group with something like:

      sudo usermod -aG docker sky

    Remember that you will have to log out and back in for this to take effect!

为了以非root用户使用docker, 可以将用户加入"docker"组.

    sudo usermod -aG docker sky

## windows下安装

参考docker官网的文章:

[http://docs.docker.com/windows/started/](http://docs.docker.com/windows/started/)

TBD: 下次在windows上试试

