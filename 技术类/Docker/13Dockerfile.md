# Dockerfile

### Dockerfile介绍

**dockerfile是用来构建docker镜像的文件！命令参数脚本！**

构建步骤：

1. 编写一个dockerfile文件
2. docker build 构建成为一个镜像
3. docker run 运行镜像
4. docker push 发布镜像（DockerHub、阿里云镜像仓库！）



很多官方镜像都是基础包，很多功能没有，我们通常会自己搭建自己的镜像！



### Dockerfile的构建过程

**基础知识：**

- 每个保留关键字（指令）都必须是大写字母
- 从上到下顺序执行
- #表示注释
- 每一个指令都会创建提交一个新的镜像层，并提交！

dockerfile是面向开发的，今后发布项目，做镜像，就需要编写dockfile文件，该文件十分简单！

Docker镜像 **springboot**

Docker镜像逐渐成为企业交付的标准，必须掌握！

**步骤：开发、部署、上线、运维**

DockerFile：构建文件，定义了一切步骤，源代码

DockerImages：通过DockerFile构建生成的镜像，最终发布运行的产品，原来是jar war

Docker容器：容器就是镜像运行起来提供服务的。



**很多指令：**

```bash
FROM        # 基础镜像
MAINTAINER  # 镜像是谁写的，姓名+邮箱
RUN         # 镜像构建时需要运行的命令
ADD         # 步骤，tomact镜像，这个tomact压缩包！添加内容，在添加时就解压包
WORKDIR     # 镜像的工作目录，可以指定
VOLUME      # 挂载的目录位置
EXPOSE      # 指定暴露端口
CMD         # 指定这个容器启动时运行的命令,只有最后一个会生效，可被覆盖
ENTRYPOINT  # 指定这个容器启动时运行的命令，启动容器时可追加命令，不可被覆盖
ONBUILD     # 当构建一个被继承DockerFile时，就会运行该指令
COPY        # 类似ADD，将我们文件拷贝到镜像中
ENV         # 构建时设置环境变量
```

### 实战测试

Docker Hub中99%的镜像都是从 FROM scratch过来的，然后配置需要的软件和配置来进行构建的。

创建一个自己的centos

```bash
vim mydockerfile
# FROM centos
# MAINTAINER zjt<597778912@qq.com>
# ENV MYPATH /usr/local    # 环境变量的目录
# WORKDIR $MYPATH
# 
# RUN yum -y install vim
# RUN yum -y install net-tools
# 
# EXPOSE 80
# CMD echo $MYPATH
# CMD echo "----end----"
# CMD /bin/bash
```

docker build -f dockerfile文件路径 -t 镜像名：[tag]



docker history id   # 查看镜像的构建历程

**CMD和ENTRYPOINT区别：**

```shell
CMD         # 指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代。
ENTRYPOINT  # 指定这个容器启动的时候要运行的命令，可以追加命令。
```

```shell
vim dockerfile-cmd-test
# FROM centos
# CMD {"ls","-a"}

# 构建镜像
docker build -f dockerfile-cmd-test -t cmdtest

不懂的话，再去看狂神。
```

### 实战：Tomcat镜像

1. 准备镜像文件tomact压缩包，jdk压缩包！
2. 编写Dockerfile文件！官方命名：Dockerfile，build会自动寻找这个文件，就不需要 -f 指定了！

```shell
FROM centos
MAINTAINER zjt<597778912@qq.com>

COPY readme.txt /usr/local/readm.txt
ADD jdk(jdk压缩包) /usr/local/    # ADD会自动解压
ADD tomcat(压缩包)  /usr/local/

RUN yum -y instal vim
ENV MYPATH /usr/local
WORKDIR $MYPATH

ENV JAVA_HOME /usr/local/jdk1.8.0_11
ENV CLASSPATH $JAVA_HOME/lib/dt.jar;$JAVA_HOME/lib/tools.jar

ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.22
ENV CATALINA_BASH /usr/local/apache-tomcat-9.0.22
ENV PATH $PATH;$JAVA_HOME/bin;$CATALINA_HOME/lib;$CATALINA_HOME/bin

EXPOSE 8080

CMD /usr/local/apache...xxx/bin/startup.sh &&tail -F /usl/local/apachexxx/bin/logs/catalina.o
```

3. 构建镜像

```shell
docker build -t diytomcat .
```

4. 启动镜像
5. 测试





























