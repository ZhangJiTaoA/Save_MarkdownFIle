# Docker网络

### 理解网络Docker0

清空所有环境

```shell
# 测试 
ip addr
# 三个网络lo，eth0，docker0
```

```shell
# docker 是如何处理容器网络的？

# linux可以ping通docker容器内部！
```

#### 原理

1. 我们每启动一个docker容器，docker就会给docker容器分配一个ip，我们只要安装了docker就会有一个网卡docker0桥接模式，使用的技术就是evth-pair技术！
2. 启动一个容器后，ip addr 后就会多一个网卡。
3. 我们发现容器带来的网卡都是一对一对的。
4. veth-pair 就是一对的虚拟设备接口，他们都是成对出现的，一段连着协议，一段彼此相连。正因为有这个特性，veth-pair 充当一个桥梁，专门用来连接各种虚拟网络设备的。
5. OpenStack，Docker容器之间的连接，OVS的连接，都是使用veth-pair技术。

#### 容器间网络连接

1. 可以互相ping通。
2. 容器和容器之间可以互相ping通。
3. 绘制网络模型图
4. docker使用的是linux的桥接，宿主机docker0是docker容器的网桥。
5. docker中的所有网络接口都是虚拟的，虚拟的转发效率高。



























