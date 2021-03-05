# PostgreSQL

Superset deployment package includes PostgreSQL and GUI tools phpPgAdmin, refer to these steps to use it:

### Manage PostgreSQL by GUI

1. Local browser Chrome or Firefox access URL: *http://server's Internet IP:9090*, enter to pgAdmin
   ![login pgAdmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/pgadmin-loginui-websoft9.png)

2. Input pgAdmin administrator account([view username and password](/stack-accounts.md#postgresql)) and enter to console
   ![pgAdmin console](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/pgadmin-console-websoft9.png)

3. Click 【server】 to connect PostgreSQL server

4. Set your PostgreSQL database connection ([don't known password](/stack-accounts.md#postgresql))
  ![set pgAdmin connection](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/pgadmin-createserver-websoft9.png)

5. Login to console successfully
  ![pgAdmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/pgadmin-console-websoft9.png)

### Manage PostgreSQL by cli

1. Use the SSH to connect your Server of Superset, then run the command `docker ps` to list all containers
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/awx/awx-getcontainerid-websoft9.png)

2. Get the container ID or Name of PostgreSQL, and use the following command to login **postgresql** container

   ```
   docker exec -it superset_db_1 psql -U superset
   ```
3. You can use any PostgreSQL commands if you have connect to **superset_db_1** container successfully

> Websoft9 provide *[PostgreSQL guide](https://support.websoft9.com/docs/postgresql/admin-phppgadmin.html)* for more useful skills of PostgreSQL, includes: modify password, create user, import/export data, enable or disable remote visit, log configuation and so on.