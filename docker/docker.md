
## 网络

### 创建网络
```bash
docker network create test
# test替换为你的网络名
```

### 查询现有网络
```bash
docker network ls
```

### 查看某个网络的连接情况
```bash
docker network inspect dataNetwork
# dataNetwork替换为你的网络
```

### 连接到网络
```bash
docker network connect dataNetwork ibeapp-build 
# dataNetwork替换为你的网络
# ibeapp-build替换为你的容器
```

### 删除网络
```bash
docker network rm test
# test替换为你的网络名
```
