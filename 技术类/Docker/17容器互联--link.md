# 容器互联--link

**每次启动docker容器，其ip地址都会重新生成，每次都更改有些繁琐，通过服务名进行连接会不会更好**

```shell
docker exec -it tomcat02 ping tomcat01
# ping不通
docker run -dit -P --name tomcat03 --link tomcat02 tomcat
docker exec -it tomcat03 ping tomcat02 # 可以ping通
```

- 通过--link就可以解决网络连接问题？
- docker network --help
- --link就是在host文件里面加入了名称和ip地址的绑定。
- 以上内容已经不推荐使用了。。。。

###### 自定义网络！不使用docker0

- docker0问题：不支持**容器名**连接访问。