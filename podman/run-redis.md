
## 使用podman启动redis

``` bash
docker run -d --restart=always --name redis \
-p 6379:6379 \
redis redis-server \
--appendonly yes \
--requirepass "redis_password"
```

### 参数解释
* -d：后台运行容器，并打印容器ID
* --restart=always：容器退出时自动重启
* --name redis：指定容器名称为redis
* -p 6379:6379：将容器的6379端口映射到主机的6379端口
* redis redis-server：启动redis容器，并指定redis-server作为容器的默认命令
* --appendonly yes：开启redis的持久化机制，将内存中的数据写入磁盘
* --requirepass "redis_password"：设置redis的密码为redis_password

