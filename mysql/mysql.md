
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

```
mysqldump --add-drop-table --skip-create-options --result-file="D:\\data\\ibe-setup-package\\setup4DongFangDianQi\\sql\\new.sql" "prj-nuclear-inspection" --ignore-table=prj-nuclear-inspection.dfdq_data_resource
```

示例：
```
SHOW TABLES LIKE 'dfdq%'
```

```
mysqldump --add-drop-table --skip-create-options --result-file="D:\\data\\ibe-setup-package\\setup4DongFangDianQi\\sql\\new.sql" "prj-nuclear-inspection" --ignore-table=prj-nuclear-inspection.dfdq_data_resource --ignore-table=prj-nuclear-inspection.dfdq_lifetime_data_1 --ignore-table=prj-nuclear-inspection
```
