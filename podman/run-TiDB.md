
## 使用podman部署TiDB集群

使用podman-compose.yml文件部署TiDB集群
``` docker-compose.yml
version: '3'

services:
  pd:
    image: pingcap/pd:latest
    container_name: my-pd
    networks:
      - tidb-network
    ports:
      - "2379:2379"
      - "2380:2380"
    command: 
      - --name=pd 
      - --client-urls=http://0.0.0.0:2379
      - --peer-urls=http://0.0.0.0:2380
      - --advertise-client-urls=http://my-pd:2379
      - --advertise-peer-urls=http://my-pd:2380

  tikv:
    image: pingcap/tikv:latest
    container_name: my-tikv
    networks:
      - tidb-network
    ports:
      - "20160:20160"
      - "20180:20180"
    command: 
      - --addr=0.0.0.0:20160 
      - --pd=http://my-pd:2379
      - --advertise-addr=my-tikv:20160
      - --advertise-status-addr=my-tikv:20180
    depends_on:
      - pd
    volumes:
      - tikv-data:/var/lib/tikv

  tidb:
    image: pingcap/tidb:latest
    container_name: my-tidb
    networks:
      - tidb-network
    ports:
      - "4000:4000"
    command: 
      - --store=tikv 
      - --path=my-pd:2379
      - --host=0.0.0.0 
      - -P=4000
    depends_on:
      - tikv
    environment:
      - TIDB_ROOT_PASSWORD=your_password
    volumes:
      - tidb-data:/var/lib/tidb

volumes:
  tikv-data:
  tidb-data:

networks:
  tidb-network:
    name: tidb-cluster-net
```

### 部署流程
``` shell
podman-compose down
podman-compose up -d
```

目前mysql密码可能没生效，需要手动改一下  
值得注意的是，宿主机需要安装mysql-client客户端  
tidb默认是没有密码的
``` shell
podman exec -it my-tidb /bin/bash
mysql -uroot -p
show databases;
use mysql;
ALTER USER 'root'@'%' IDENTIFIED BY 'new_password';
```
