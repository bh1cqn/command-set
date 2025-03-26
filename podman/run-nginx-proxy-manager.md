
## 使用podman部署nginx-proxy-manager

使用podman-compose.yml文件部署nginx-proxy-manager

[官网地址](https://nginxproxymanager.com/)  
[github地址](https://github.com/NginxProxyManager/nginx-proxy-manager)

``` docker-compose.yml
version: '3'

services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      # These ports are in format <host-port>:<container-port>
      - '80:80' # Public HTTP Port
      - '443:443' # Public HTTPS Port
      - '81:81' # Admin Web Port
      # Add any other Stream port you want to expose
      # - '21:21' # FTP

    environment:
      # Uncomment this if you want to change the location of
      # the SQLite DB file within the container
      # DB_SQLITE_FILE: "/data/database.sqlite"

      # Uncomment this if IPv6 is not enabled on your host
      # DISABLE_IPV6: 'true'

    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

### 部署流程



可能需要前置的创建两个文件夹，data和letsencrypt
``` shell
mkdir data
mkdir letsencrypt
```
启动容器
``` shell
podman-compose down
podman-compose up -d
```