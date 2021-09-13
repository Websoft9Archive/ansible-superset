---
sidebarDepth: 3
---

# 参数

Superset 预装包包含 Superset 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

## 路径

本项目出 Nginx 之外，所有组件均基于 Docker 安装，运行 `docker ps` 命令查看所有组件：

```
CONTAINER ID   IMAGE                           COMMAND                  CREATED              STATUS                                 PORTS                               NAMES
453f04935734   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            0.0.0.0:8088->8088/tcp              superset_app
5477e7693ef3   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            8088/tcp                            superset_worker
d6670fa1bc11   apache/superset:latest          "/usr/bin/docker-ent…"   About a minute ago   Up About a minute (healthy)            8088/tcp                            superset_worker_beat
17689f5d6ebb   postgres:10                     "docker-entrypoint.s…"   About a minute ago   Up About a minute                      0.0.0.0:5432->5432/tcp              superset_db
06bf52f4b856   redis:3.2                       "docker-entrypoint.s…"   About a minute ago   Up About a minute                      127.0.0.1:6379->6379/tcp            superset_cache
```

### Superset

Superset 源码目录：*/data/wwwroot/superset*  
Superset 数据目录：*/data/wwwroot/superset_home*  
Superset 配置目录：*/data/wwwroot/superset/docker*  
Superset 配置文件： */data/wwwroot/superset/docker/pythonpath_dev/superset_config.py*  

> 配置目录包括数据库连接信息、[Superset 配置文件](https://github.com/apache/superset/blob/master/superset/config.py)等

### Nginx

Nginx 虚拟主机配置文件：*/etc/nginx/conf.d/default.conf*  
Nginx 主配置文件： */etc/nginx/nginx.conf*  
Nginx 日志文件： */var/log/nginx*  
Nginx 伪静态规则目录： */etc/nginx/conf.d/rewrite*

### PostgreSQL

PostgreSQL 主目录：*/data/wwwroot/superset/postgresql*  

> 包含所有 PostgreSQL 数据文件和配置文件

#### pgAdmin

pgAdmin 主目录：*/data/apps/pgadmin*  

### Docker

Docker 根目录: */var/lib/docker*  
Docker 镜像目录: */var/lib/docker/image*   
Docker 存储卷：*/var/lib/docker/volumes*  

### Docker Compose

本环境使用 Docker Compose 作为容器编排（调度）工具，用于管理多个容器的启动和服务连接。

Docker Compose 命令位置：*/usr/local/bin/docker-compose*  
Docker Compose 配置目录 */data/wwwroot/superset* 

## 端口号

在云服务器中，通过 **[安全组设置](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** 来控制（开启或关闭）端口是否可以被外部访问。 

通过命令`netstat -tunlp` 看查看相关端口，下面列出可能要用到的端口：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| TCP | 8088 | Superset 端口 | 可选 |
| TCP | 80 | 通过 HTTP 访问 Superset | 可选 |
| TCP | 443 | 通过 HTTPS 访问 Superset | 可选 |
| TCP | 5432 | 通过 TCP 访问 PostgreSQL数据库 | 可选 |
| TCP | 9090 | PostgreSQL 可视化管理工具 pgAdmin | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

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
