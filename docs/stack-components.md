# Parameters

The Superset deployment package contains a sequence software (referred to as "components") required for Superset to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path

All components installed on Docker except for **Nginx**..

Use **SSH** to connect Server and run the command `docker ps`, you can list all containers:

```
CONTAINER ID   IMAGE                           COMMAND                  CREATED              STATUS                                 PORTS                               NAMES
453f04935734   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            0.0.0.0:8088->8088/tcp              superset_app
5477e7693ef3   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            8088/tcp                            superset_worker
d6670fa1bc11   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            8088/tcp                            superset_worker_beat
17689f5d6ebb   postgres:10                     "docker-entrypoint.s…"   About a minute ago   Up About a minute                      0.0.0.0:5432->5432/tcp              superset_db
06bf52f4b856   redis:3.2                       "docker-entrypoint.s…"   About a minute ago   Up About a minute                      127.0.0.1:6379->6379/tcp            superset_cache
```

## Path

### Superset

Superset repository directory: */data/wwwroot/superset*  
Superset data directory: */data/wwwroot/superset_data*  
Superset configuration directory: */data/wwwroot/superset/docker*  
Superset configuration file: */data/wwwroot/superset/docker/pythonpath_dev/superset_config.py*  

> Superset configuration directory includes: *configuration files, env, init script.*

### Nginx

Nginx vhost configuration file: */etc/nginx/conf.d/default.conf*  
Nginx main configuration file: */etc/nginx/nginx.conf*  
Nginx log file: */var/log/nginx*  

### PostgreSQL

PostgreSQL directory: */data/wwwroot/superset/postgresql*  

> PostgreSQL directory includes data and configuration files

#### pgAdmin

pgAdmin directory: */data/apps/pgadmin*  

### Docker

Docker root directory: */var/lib/docker*  
Docker image directory: */var/lib/docker/image*   
Docker volumes: */var/lib/docker/volumes*  

## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

You can run the cmd `netstat -tunlp` to list all used ports, and we list the following most useful ports:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| HTTP | 8161 | HTTP requests for Superset Console| Required |
| HTTPS | 5672 | epmd | Optional |
| TCP | 8088 | Superset | Optional |
| TCP | 80 | HTTP access Superset | Optional |
| TCP | 443 | HTTPS access Superset | Optional |
| TCP | 9090 | PostgreSQL Web-GUI tool | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Check all components version
sudo cat /data/logs/install_version.txt

# Linux Version
lsb_release -a

# Nginx  Version
nginx -V

# Docker Version
docker -v

# Superset Version
docker exec -it superset_app /bin/bash -c 'cat /app/superset-frontend/package.json |grep version'

# PostgreSQL version
docker exec -it superset_db /bin/bash -c 'psql -V'
```