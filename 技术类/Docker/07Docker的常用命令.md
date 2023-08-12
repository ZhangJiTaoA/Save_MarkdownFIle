## Docker的常用命令

### 帮助命令

```shell
docker version      # 显示docker的版本信息
docker info         # 显示docker的系统信息，包括镜像和容器的数量
docker 命令 --help   # 万能命令
```

帮助文档的地址：

[Reference documentation | Docker Documentation](https://docs.docker.com/reference/)

## 镜像命令

```shell
docker images   # 查看本机所有已下载的镜像

# 解释
REPOSITORY  镜像的仓库源
TAG         镜像的标签
IMAGE  ID   镜像的id
CREATED     镜像的创建时间
SIZE        镜像的大小

# 可选项
-a        # 显示所有的镜像
-q        # 只显示镜像的id
```

```shell
docker search mysql    # 搜索镜像


# 可选项
--filter=STARS=3000   # 搜索starts大于3000的

```

```shell
docker pull mysql:[tag]    # 下载mysql,如果不写tag，默认版本是latest

# 分层下载，docker image的核心  联合文件系统

# 可选项
docker pull mysql:5.7    # 指定版本下载
```

```shell
docker rmi -f [id]      # 通过镜像id删除镜像，空格可以删除多个镜像
docker rmi -f $(docker images -aq)  # 删除全部镜像
```



## 容器命令

**说明：有了镜像才可以创建容器，Linux，下载一个centos镜像来测试学习**

```shell
docker pull centos     # 下载一个centos
```



```shell
docker run [可选参数] image

# 参数说明
--name="Name"   容器名字，用来区分容器
-d              后台方式运行，
-it             使用交互方式运行
-p              指定容器的端口   -p  8080[主机端口]:8080[容器端口]
-P              随机指定端口

# 测试
docker run -it centos /bin/bash    # 以交互方式运行，启动并进入容器
exit          # 退出容器

# 列出所有运行的容器
docker ps
# 参数说明
    # 当前运行的容器
-a  # 列出正在运行的容器+带出历史运行过的容器
-n=？# 显示最近创建的n个容器
-q  # 只显示容器的编号
```

```shell
# 退出容器
exit  # 容器直接停止并退出
ctrl+p+q  # 容器不停止退出
```

```shell
# 删除容器
docker rm 容器id   # 删除指定的容器，不能删除正在运行的容器，-f可强制删除
docker rm -f $(docker ps -aq)  # 删除指定容器
docker ps -a -q | xargs docker rm  # 删除所有容器
```

```shell
# 启动和停止容器
docker start 容器id    # 启动容器
docker restart 容器id  # 重启容器 
docker stop 容器id     # 停止当前正在运行的容器
docker kill 容器id     # 强制停止当前正在运行的容器
```

#### 常用其他命令

```shell
# 后台启动
docker run -d centos   # 通过该方式后台启动，通过docker ps发现停止了

# 常见的坑，docker容器使用后台运行，就必须有一个前台的进行，docker发现没有应用，就会自动停止。
# nginx，容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了
```

```shell
# 查看日志
docker logs

# 显示日志
-tf        # 显示日志，带上时间戳
--tail  n   # 显示n行日志 
```

```shell
# 查看容器中的进程信息
docker top 容器id   
```

```shell
# 查看容器内部信息，元数据
docker inspect 容器id
```

```shell
# 进入当前正在运行的容器
docker exec -it 容器id bashshell   # 进入容器，进入容器后开启一个新的终端，可在里面操作

docker attach 容器id     #  进入容器，进入容器正在执行的终端，不会自动开启新终端。

```

```shell
# 主机和docker内部互相拷贝
docker cp 容器id:路径    # 将容器内文件拷贝到主机当前地址
```



### 小结

![Docker技术( 容器虚拟化技术 )-云计算-火龙果软件](https://ts1.cn.mm.bing.net/th/id/R-C.da128e7d249204ab348c12bd3cb89d43?rik=i%2f0w6e0%2bWfyMVA&riu=http%3a%2f%2fwww.uml.org.cn%2fyunjisuan%2fimages%2f2019102918.png&ehk=X8dgvhwZCKhqnqp0hoYBzGhzAOqI7k5Iatm84%2fXSYIk%3d&risl=&pid=ImgRaw&r=0)















