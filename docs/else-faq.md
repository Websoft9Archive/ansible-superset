# FAQ

####  Does Superset support multiple languages?

Yes, but dev version only English

#### How can I get all service for this solution?

```
sudo docker ps -a
```

#### How can I running Superset container as root user?

```
docker exec -it --user root superset_app bash
```

#### Can I reset password of Superset by command?

No, you should modify it by Superset console

#### If there is no domain name, can I deploy Superset?

Yes, visit Superset by *http://Instance's Internet IP*

#### What is the password for the database root user?

The password is stored in the server related file: `/credentials/password.txt`

#### Is there a web-base GUI database management tools?

Yes, pgAdmin is on it, visit by *http://Instance's Internet IP:9090*

#### Is it possible to modify the source path of Superset?

No

#### How to change the permissions of filesytem?

Change owner(group) or permissions like below:

```shell
chown -R superset.superset /data/wwwroot/superset
find /data/wwwroot/superset -type d -exec chmod 750 {} \;
find /data/wwwroot/superset -type f -exec chmod 640 {} \;
```

#### What's the difference between Deployment and Installation?

- Deployment is a process of installing and configuring a sequence of software in sequence in a different order, which is a complex system engineering.  
- Installation is the process of starting the initial wizard after the application is prepared.  
- Installation is simpler than deployment. 

#### What's Cloud Platform?

Cloud platform refers to platform manufacturers that provide cloud computing services, such as: **Azure, AWS, Alibaba Cloud, HUAWEI CLOUD, Tencent Cloud**, etc.

#### What is the difference between Instance, Cloud Server, Virtual Machine, ECS, EC2, CVM, and VM?

No difference, just the terminology used by different manufacturers, actually cloud servers