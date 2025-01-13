
## 用户相关

### 修改密码
```sql
ALTER USER 'username'@'localhost' IDENTIFIED BY 'new_password';
```




## 权限相关

### 修改用户连接权限
```sql
SELECT user, host FROM mysql.user WHERE user = 'your_username'; # 查询用户
UPDATE mysql.user SET host = 'localhost' WHERE user = 'your_username' AND host = '%'; # 根据查询信息写where语句
FLUSH PRIVILEGES;
```

### 解除所有权限
```sql
REVOKE ALL PRIVILEGES ON *.* FROM 'username'@'%';
```

### 授予所有权限
```sql
GRANT ALL PRIVILEGES ON `schema`.* TO 'username'@'%';
```

