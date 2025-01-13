
## 用户相关

### 修改密码
```sql
ALTER USER 'username'@'localhost' IDENTIFIED BY 'new_password';
```

## 权限相关

### 解除所有权限
```sql
REVOKE ALL PRIVILEGES ON *.* FROM 'username'@'%';
```

### 授予所有权限
```sql
GRANT ALL PRIVILEGES ON `schema`.* TO 'username'@'%';
```
[//]: # (todo-hzx 上边这个反引号待优化)