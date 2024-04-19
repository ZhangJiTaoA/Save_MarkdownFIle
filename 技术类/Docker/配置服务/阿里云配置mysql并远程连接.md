### 阿里云配置mysql并远程连接

1. **下载并运行镜像**

```bash
docker run -it --name mysql_5.7 -e MYSQL_ROOT_PASSWORD=123456 -P 3306:3306 -d mysql:5.7
```

2. **查看镜像信息**

```bash
docker ps -a
```

3. **进入容器**

```bash
docker exec -it mysql_5.7 /bin/bash
```

4. **启动mysql**

```bash
mysql -uroot -p123456
```

5. **查看用户信息**

```sql
select host,user,plugin,authentication_string from mysql.user;
```

==做到这一步，再配置阿里云3306端口即可成功远程连接到数据库==

6. **授权步骤**

（未实践）

```sql
ALTER user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
// 如果以上内容不起作用，可能是版本问题，可试试以下语句
grant all privileges on *.* to 'root'@'%' identified by '123456' with grant option;
```

7. **刷新**

（未实践）

```sql
FLUSH PRIVILEGES;
```

8. **配置阿里云的3306端口**