---
date: 2019-01-27T07:30:00+08:00
title: port命令
weight: 349
menu:
  main:
    parent: "command-container"
description : "Docker的port命令"
---

### 介绍

https://docs.docker.com/engine/reference/commandline/port/

列出容器的端口映射或特定映射

### 使用

```bash
docker port CONTAINER [PRIVATE_PORT[/PROTO]]
```

### 示例

```bash
$ docker port test
$ docker port test 7890/tcp
$ docker port test 7890/udp
$ docker port test 7890
```

