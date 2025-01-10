docker run -d --restart=always --name mysql \
-p 3306:3306 \
-v /home/mysql/conf:/etc/mysql/mysql.conf.d \
-v /home/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=mysql_password \
-e TZ=Asia/Shanghai \
mysql:8 --lower-case-table-names=1


