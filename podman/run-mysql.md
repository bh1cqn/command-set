## 使用podman启动mysql

``` bash
podman run -d --restart=always --name mysql \
-p 3306:3306 \
-v /home/mysql/conf:/etc/mysql/mysql.conf.d \
-v /home/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=mysql_password \
-e TZ=Asia/Shanghai \
mysql:8 --lower-case-table-names=1
```

### 参数解释
* -d：后台运行容器，并打印容器ID
* --restart=always：容器退出时自动重启
* --name mysql：指定容器名称为mysql
* -p 3306:3306：将容器的3306端口映射到主机的3306端口
* -v /home/mysql/conf:/etc/mysql/mysql.conf.d：将主机的/home/mysql/conf目录挂载到容器的/etc/mysql/mysql
* -v /home/mysql/data:/var/lib/mysql：将主机的/home/mysql/data目录挂载到容器的/var/lib/mysql
* -e MYSQL_ROOT_PASSWORD=mysql_password：设置root用户的密码为mysql_password
* -e TZ=Asia/Shanghai：设置时区为上海时区
* mysql:8：指定要运行的镜像名称，这里使用mysql:8镜像
* --lower-case-table-names=1：设置mysql数据库表名是否区分大小写，设置为1表示不区分大小写，设置为0表示区分大小写。