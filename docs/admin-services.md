# Start or Stop the Services

These commands you must know when you using the Superset of Websoft9

> You can run the command `sudo docker ps` to inquire the container's name before manage service

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

### phpPgAdmin

```shell
sudo docker start pgadmin
sudo docker stop pgadmin
sudo docker restart pgadmin
```