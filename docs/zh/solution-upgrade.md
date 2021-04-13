# 更新升级

网站技术日新月异，**更新升级**是维护工作之一，长时间不升级的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。  

这里注意更新与升级这两词的差异（[延伸阅读](https://support.websoft9.com/docs/faq/zh/tech-upgrade.html#更新-vs-升级)），例如：
- 操作系统打个补丁常称之为**更新**，Ubuntu16.04 变更为 Ubuntu18.04，称之为**升级**
- MySQL5.6.25-->MySQL5.6.30 常称之为**更新**，MySQL5.6->MySQL5.7 称之为**升级**

Superset 完整的更新升级包括：系统级更新（操作系统和运行环境）和 Superset 程序升级两种类型

## 系统级更新

运行一条更新命令，即可完成系统级更新：

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y --skip-broken
```
> 本部署包已预配置一个用于自动更新的计划任务。如果希望去掉自动更新，请删除对应的Cron


## Superset 升级

Superset 采用 Docker 部署，其升级流程：拉取镜像 > 删除容器 > 重建容器

> 升级之前请完成服务器的快照备份，以防不测。

1. 使用 SSH 登录服务，进入到 Superset 目录后，拉取最新版本镜像
   ```
   cd /data/wwwroot/superset
   docker-compose pull
   ```
   > 系统会自动拉取最新版镜像，如果没有镜像可拉取，则无需更新

2. 停止并删除当前的 Superset 容器

   ```
   docker-compose down -v
   ```

3. 重新创建 Superset 容器
   ```
   docker-compose up -d
   ```