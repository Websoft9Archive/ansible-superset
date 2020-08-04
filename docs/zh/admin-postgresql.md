# PostgreSQL

Seafile 预装包中内置 PostgreSQL 容器以及可视化管理工具 phpPgAdmin。  

本部署方案支持如下两种 PostgreSQL 管理方式：

## 可视化管理

1. 本地浏览器 Chrome 或 Firefox 访问：*http://服务器公网IP:9090*，进入phpPgAdmin。
  ![登录phpPgadmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/phppgadmin-login-websoft9.png)

2. 输入数据库用户名和密码([不知道密码？](/zh/stack-accounts.md#postgresql))

3. 开始管理数据库
  ![管理phpPgadmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/postgresql/phppgadmin-console-websoft9.png)

## 命令管理

可以登录容器后使用命令对 phpPgAdmin。 进行操作。

1. 使用 SSH 登录服务器后，运行`docker ps`命令获取 Name 或 ID

2. 进入 postgresql 容器操作界面

   ```
   docker exec -it superset_db_1 psql -U superset
   ```
3. 接下来可以使用命令操作 PostgreSQL 

> 阅读 Websoft9 提供的 [《PostgreSQL教程》](https://support.websoft9.com/docs/postgresql/zh/) ，掌握更多的 PostgreSQL 实用技能：修改密码、导入/导出数据、创建用户、开启或关闭远程访问、日志配置等