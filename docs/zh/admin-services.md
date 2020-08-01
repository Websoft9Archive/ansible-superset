# 服务启停

使用由Websoft9提供的 Superset 部署方案，可能需要用到的服务如下：

### Superset

```shell
sudo systemctl start superset-server
sudo systemctl stop superset-server
sudo systemctl restart superset-server
sudo systemctl status superset-server

# you can use this debug mode if Superset service can't run
superset-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```
