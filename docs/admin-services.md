# Start or Stop the Services

These commands you must know when you using the Superset of Websoft9

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
sudo systemctl start redis
sudo systemctl stop redis
sudo systemctl restart redis
sudo systemctl status redis
```
