# PostgreSQL

Superset deployment package includes PostgreSQL and GUI tools phpPgAdmin, refer to these steps to use it:

### Manage PostgreSQL by GUI

1. Using the Chrome or FireFox to visit URL *http://Internet IP:9090*
  ![log in phpPgadmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/phppgadmin-login-websoft9.png)
3. Enter username and password of MySQL([Don't known password?](/stack-accounts.md))
4. Start to manage PostgreSQL
  ![phpPgadmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/phppgadmin-console-websoft9.png)

### Manage PostgreSQL by CMD

1. Use the SSH to connect your Server of Seafile, then run the command `docker ps` to list all containers
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/awx/awx-getcontainerid-websoft9.png)

2. Get the container ID or Name of PostgreSQL, and use the following command to login **postgresql** container

   ```
   docker exec -it superset_db_1 psql -U superset
   ```
3. You can use any MySQL commands if you have connect to **seafile-mysql** container successfully

> Websoft9 provide *[PostgreSQL guide](https://support.websoft9.com/docs/postgresql/admin-phppgadmin.html)* for more useful skills of PostgreSQL, includes: modify password, create user, import/export data, enable or disable remote visit, log configuation and so on.