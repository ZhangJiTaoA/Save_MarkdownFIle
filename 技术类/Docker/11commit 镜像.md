# commit 镜像

```shell
docker commit 提交容器成为一个新的副本
docker commit -m="提交的描述信息"  -a="作者"  容器id  目标镜像名:[TAG]
```

**实战测试**

```shell
# 启动一个默认的tomcat
# 默认的tomcat是没有webapps应用的，
# 自己拷贝东西进去。
# 将修改后的容器通过commit提交为一个新的镜像！以后就使用修改过的镜像即可。
```

```shell
如果想保存当前容器的状态，可以通过commit来提交，获得一个镜像。
就好比以前vm时的快照。
```

**才算入门docker**







学习方法：理解概念，但是一定要**实践**，最后实践理论**螺旋上升**，get到知识。