---
layout: default
title:  "Docker相关知识笔记"
date:   2020-12-08 14:32:50 +0800
categories: notes
excerpt："1.在容器中使用systemctl服务"
---
#### 1.在容器中使用systemctl服务
启动容器时，`-d` 后跟上 `--privileged` ，并使用 `/usr/sbin/init` 作为启动命令。
例如：
```shell
docker run -it --name container_name -d --privileged image-name /usr/sbin/init
```
>`--privileged=true`：可以docker内真正拥有root权限
>`/usr/sbin/init`：可以在docker内使用systemctl命令
>当用户执行 `docker run --privileged` 时，Docker 将启用对主机上所有设备的访问，并在 AppArmor 或 SELinux 中进行一些配置，以允许容器对主机的访问几乎与在主机上容器外部运行的进程相同。
>[文档链接](https://docs.docker.com/engine/reference/run/)