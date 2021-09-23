# Update & Upgrade

Updates and upgrades are one of the maintenance tasks for sytem. Programs that are not upgraded for a long time, like buildings that are not maintained for a long time, will accelerate aging and gradually lose functionality until they are unavailable.

You should know the differences between the terms **Update** and **Upgrade**([Extended reading](https://support.websoft9.com/docs/faq/tech-upgrade.html#update-vs-upgrade))
- Operating system patching is **Update**, Ubuntu16.04 to Ubuntu18.04 is **Upgrade**
- MySQL5.6.25 to MySQL5.6.30 is **Update**, MySQL5.6 to MySQL5.7 is **Upgrade**

For Superset maintenance, focus on the following two Update & Upgrade jobs

- Sytem update(Operating System and Running Environment) 
- Superset upgrade 

## System Update

Run an update command to complete the system update:

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y --skip-broken
```
> This deployment package is preconfigured with a scheduled task for automatic updates. If you want to remove the automatic update, please delete the corresponding Cron

## Superset Upgrade

This deployment solution is based on Docker and so you can upgrade Superset by the standard process of Docker:  

> You should complete a snapshot backup before upgrade

1. Use **SSH** to login Server, cd to the directory of docker-compose file, then stop the containers
   ```
   cd /data/wwwroot/superset
   docker-compose down
   ```
2. Back up and update docker startup related files
   ```
   mv  /data/wwwroot/superset/docker /data/wwwroot/superset/docker_bark
   mkdir superset-latest
   cd superset-latest
   git clone https://github.com/Websoft9/docker-superset.git
   cp -R docker-superset/docker /data/wwwroot/superset
   ```

3. Update to the version you want to upgrade to(Notice: you cannot use latest as the version number)

   ```
   cd /data/wwwroot/superset
   sed -i "s/APP_VERSION=old_version/APP_VERSION=new_version/g" /data/wwwroot/superset/.env
   ```
4. Recreate containers
   ```
   docker-compose up -d
   ```
