# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Domain binding

The precondition for binding a domain is that Superset can accessed by domain name.

Nonetheless, from the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

Superset domain name binding steps:

1. Connect your Server by SFTP tool

2. Modify [Nginx vhost configuration file](/stack-components.md#nginx), change the **server_name**'s value to your domain name
   ```text
   server
   {
   listen 80;
   server_name www.example.com;  # 此处修改为你的域名
   ...
   }
   ```
3. Restart Nginx service
   ```
   sudo systemctl restart nginx
   ```


## Install Database Drivers

You’ll need to install the required packages for the database you want to use as your metadata database as well as the packages needed to connect to the databases.  

The below is the command how to install drivers

```
# Access Superset container as root user
docker exec -it --user root superset_app bash

# sample1
pip install mysqlclient

# sample2
pip install psycopg2	
```

Refer to more [Supported Databases and Dependencies](https://superset.apache.org/docs/databases/installing-database-drivers)

## Resetting Password

There are two main measures to reset password.

### Changing password

Take the steps below:

Login to Superset console, open:【Settings】>【User】>【Info】 to modify password

![Superset modify password](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-resetpw-websoft9.png)


### Forgot Password

Try to retrieve your password by the flowing steps:  

1. Use **SSH** to connect Server, run the below command to login database
   ```
   docker exec -it superset_db psql -U superset
   ```

2. At the mode of **Database CLI interaction**, run the below SQL command, then you password is `admin123` now.
   ```
   update ab_user set password='pbkdf2:sha256:150000$w8vfDHis$b9c8fa353137417946766ed87cf20510da7e1e3a7b79eef37426330abef552bf' where username='admin';
   ```



## Replace Logo

If you want to replace logo of Superset Container, please refer to below steps:  

1. Use **SFTP** to upload you png logo to the directory */data` 

2. Rename it to *superset-logo-horiz*

3. Run the below command to replace Superset official logo
   ```
   docker cp /data/superset-logo-horiz.png superset_app:/app/superset/static/assets/images/superset-logo-horiz.png
   ```
   > superset_app is the  SuperSet container name

4. Refresh the Superset console
