# PostgreSQL

Superset 预装包中内置 PostgreSQL 容器以及可视化管理工具 pgAdmin。  

本部署方案支持如下两种 PostgreSQL 管理方式：

## 可视化管理

1. 本地浏览器 Chrome 或 Firefox 访问：*http://服务器公网IP:9090*，进入 pgAdmin
   ![登录pgAdmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/postgresql/pgadmin-loginui-websoft9.png)

2. 输入 pgAdmin 管理员的用户名和密码([查看账号密码](/zh/stack-accounts.md#postgresql))之后，进入控制台
   ![pgAdmin 控制台](https://libs.websoft9.com/Websoft9/DocsPicture/zh/postgresql/pgadmin-console-websoft9.png)

3. 在控制台点击【添加服务器】，连接PostgreSQL服务器

4. 设置所需管理的 PostgreSQL 数据库连接信息([不知道密码？](/zh/stack-accounts.md#postgresql))
  ![设置pgAdmin连接信息](https://libs.websoft9.com/Websoft9/DocsPicture/zh/postgresql/pgadmin-setconnection-websoft9.png)

5. 成功连接
  ![pgAdmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/postgresql/pgadmin-console-websoft9.png)

## 命令管理

可以登录容器后使用命令对 PostgreSQL 进行操作。

1. 使用 SSH 登录服务器后，运行`docker ps`命令获取 Name 或 ID

2. 进入 postgresql 容器操作界面

   ```
   docker exec -it superset_db_1 psql -U superset
   ```
3. 接下来可以使用命令操作 PostgreSQL 

> 阅读 Websoft9 提供的 [《PostgreSQL教程》](https://support.websoft9.com/docs/postgresql/zh/) ，掌握更多的 PostgreSQL 实用技能：修改密码、导入/导出数据、创建用户、开启或关闭远程访问、日志配置等