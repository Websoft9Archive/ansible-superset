# Start or Stop the Services

These commands you must know when you using the Superset of Websoft9

> You can run the command `sudo docker ps` to inquire the container's name before manage service

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