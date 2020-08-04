# Parameters

The Superset deployment package contains a sequence software (referred to as "components") required for Superset to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path

All components installed on Docker except for **Nginx**..

Use **SSH** to connect Server and run the command `docker ps`, you can list all containers:

```
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS                          PORTS                              NAMES
1fb7b1a37109        superset_postgre          "/usr/bin/docker-ent…"   3 hours ago         Up 3 hours (healthy)            8080/tcp, 0.0.0.0:8088->8088/tcp   superset_postgre_1
195016610b1e        superset_postgre-worker   "/usr/bin/docker-ent…"   3 hours ago         Restarting (1) 47 seconds ago                                      superset_postgre-worker_1
ca55ed7b73bf        postgres:10               "docker-entrypoint.s…"   3 hours ago         Up 3 hours                      127.0.0.1:5432->5432/tcp           superset_db_1
0d6b6c901f6a        redis:3.2                 "docker-entrypoint.s…"   3 hours ago         Up 3 hours                      127.0.0.1:6379->6379/tcp           superset_redis_1
7746c6e4aa7d        dockage/phppgadmin        "/sbin/entrypoint ap…"   24 hours ago        Up 6 hours                      443/tcp, 0.0.0.0:9090->80/tcp      phppgadmin
```

## Path

### Superset

Superset repository directory: */data/wwwroot/superset*  
Superset data directory: */data/wwwroot/superset_data*  
Superset configuration file: */data/wwwroot/superset/docker/pythonpath_dev/superset_config.py*  

Superset data directory is the volumes for data long-time storage, includes: *database data, Superset configuration file, environment variable, init script.*

### Nginx

Nginx vhost configuration file: */etc/nginx/conf.d/default.conf*  
Nginx main configuration file: */etc/nginx/nginx.conf*  
Nginx log file: */var/log/nginx*  

### PostgreSQL

PostgreSQL data storage: */data/wwwroot/superset_data/volumes/superset_db_home*  

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
| TCP | 8088 | Superset 端口 | 可选 |
| TCP | 80 | 通过 HTTP 访问 Superset | 可选 |
| TCP | 443 | 通过 HTTPS 访问 Superset | 可选 |
| TCP | 9090 | PostgreSQL 可视化管理工具 phpPgAdmin | 可选 |


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
```
