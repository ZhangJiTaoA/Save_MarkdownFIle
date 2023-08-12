## Docker安装

##### Docker的基本组成

![Docker 快速入门系列-Docker的基本组成](https://cdn.learnku.com/uploads/images/202003/18/22215/v7N8wg4sy3.png!large)

一个镜像可以启动多个容器。

镜像：image

- docker镜像就好像是一个模板，可以通过这个模板创建容器服务，tomcat镜像===》run===》tomcat01容器（提供服务器）
- 通过这个镜像可以创建多个容器（最终服务运行或项目运行就是在容器中）

容器：container

- Docker利用容器技术，独立运行一个或一个组应用，通过镜像来创建
- 启动、停止、删除，基本命令！
- 目前可以把这个容器理解为一个简易的linux系统

仓库：repository

- 存放镜像的地方！
  - 公有仓库
    - Docker Hub（默认是国外的）
    - 阿里云等（配置镜像加速）
  - 私有仓库



#### 安装Docker

```
环境准备
```

1. 需要会一点linux的基础！
2. CentOS 7
3. 使用远程连接工具对服务器进行操作！

```shell
环境查看
cat /etc/os-release
uname -r  # 查看环境
```

```shell
查看帮助文档即可
# 阿里云镜像地址
# http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

```shell
systemctl start docker  # 启动docker服务
docker run hello-world  # 验证是否安装成功
```

```shell
查看一下下载的镜像在不在
docker images
```

卸载docker

```shell
查看帮助文档即可
```



## 阿里云镜像加速

1. 登录阿里云，找到容器服务！
2. 找到镜像加速位置！
3. 配置使用！
4. 据说开始收费了！







































