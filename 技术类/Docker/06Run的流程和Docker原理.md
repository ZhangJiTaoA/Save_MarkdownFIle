## Run的流程和Docker原理

#### 回顾HelloWorld流程



#### 底层原理

**Docker是怎么工作的？**

Docker是一个CS结构的系统，Docker的守护进程（服务）运行在我们主机上，通过Socket从客户端访问！

DockerServer接收到DockerClient的指令，就会执行这个命令！



**Docker为什么比虚拟机快？**

1. Docker有着比虚拟机更少的抽象层！
2. Docker利用的是宿主机的内核！vm需要Guest OS！新建容器时，Docker无需加载一个操作系统内核。
3. 