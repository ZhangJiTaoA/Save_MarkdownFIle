## Run的流程和Docker原理

#### 回顾HelloWorld流程



#### 底层原理

**Docker是怎么工作的？**

Docker是一个CS结构的系统，Docker的守护进程（服务）运行在我们主机上，通过Socket从客户端访问！

DockerServer接收到DockerClient的指令，就会执行这个命令！



**Docker为什么比虚拟机快？**

1. Docker有着比虚拟机更少的抽象层！
2. Docker利用的是宿主机的内核！vm需要Guest OS！新建容器时，Docker无需加载一个操作系统内核。





**docker-和宿主机**

```shell
docker inspect name  # 找到Pid
ps -ef | grep 找到的Pid  # 一个容器在宿主机看来就是一个进程
```



**namespace隔离**

- IPC：隔离进程间通信资源
- NET：网络设备，协议栈，端口
- PID：进程号
- USER：用户/组
- UTS：主机名及域名























