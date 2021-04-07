# 服务启停

使用由Websoft9提供的 Superset 部署方案，可能需要用到的服务如下：

> 先通过 `sudo docker ps` 命令查看容器名称

### Superset

```shell
sudo docker start superset_postgre_1
sudo systemctl stop superset_postgre_1
sudo systemctl restart superset_postgre_1
```

### PostgreSQL

```shell
sudo docker start superset_db_1
sudo docker stop superset_db_1
sudo docker restart superset_db_1
```

### Redis

```shell
sudo docker start superset_redis_1
sudo docker stop superset_redis_1
sudo docker restart superset_redis_1
```

### pgAdmin

```shell
sudo docker start pgadmin
sudo docker stop pgadmin
sudo docker restart pgadmin
```