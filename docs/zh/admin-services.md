# 服务启停

使用由Websoft9提供的 Superset 部署方案，可能需要用到的服务如下：

> 先通过 `sudo docker ps` 命令查看容器名称

### Docker-compose

```
sudo docker-compose stop
sudo docker-compose restart
```

### Superset

```shell
sudo docker start superset_app
sudo docker stop superset_app
sudo docker restart superset_app
sudo docker stats superset_app
```

### PostgreSQL

```shell
sudo docker start superset_db
sudo docker stop superset_db
sudo docker restart superset_db
sudo docker stats superset_db
```

### Redis

```shell
sudo docker start superset_cache
sudo docker stop superset_cache
sudo docker restart superset_cache
sudo docker stats superset_cache
```

### pgAdmin

```shell
sudo docker start pgadmin
sudo docker stop pgadmin
sudo docker restart pgadmin
```