# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

当服务器上只有一个网站时，不做域名绑定也可以访问网站。但从安全和维护考量，**域名绑定**不可省却。

以示例网站为例，域名绑定操作步骤如下：

1. 确保域名解析已经生效  
2. 使用 SFTP 工具登录云服务器
2. 修改 [Nginx虚拟机主机配置文件](/zh/stack-components.md#nginx)，将其中的 **server_name** 项的值修改为你的域名
   ```text
   server
   {
   listen 80;
   server_name www.example.com;  # 此处修改为你的域名
   ...
   }
   ```
3. 保存配置文件，重启 [Nginx 服务](/zh/admin-services.md#nginx)

## 配置文件

Superset 配置文件 [superset_config.py](https://github.com/apache/superset/blob/master/superset/config.py) 是自定义配置 Superset 功能的主要入口。

## 安装数据库驱动

Superset 支持数十种数据库，但 Superset Docker 镜像默认并没有安装[数据库的驱动](https://superset.apache.org/docs/databases/installing-database-drivers)（连接程序）。  

因此，需要用户进入到容器后手动安装，具体如下：

```
# 进入 Superset 容器，以 root 身份运行命令
docker exec -it --user root superset_app bash

# 范例：安装 MySQL 驱动
pip install mysqlclient

# 范例：安装 PostgreSQL 驱动
pip install psycopg2	
```

更多驱动参考官方[Database dependencies](https://superset.apache.org/docs/databases/installing-database-drivers)

## 重置密码

常用的 Superset 重置密码相关的操作主要有修改密码和找回密码两种类型：

### 修改密码

登录 Superset 后台，修改密码：【Settings】>【User】>【Info】

![Superset 修改密码](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-resetpw-websoft9.png)

### 找回密码

如果用户忘记了密码，需要通过修改数据库中的数据表的方式找回：

1. 使用 **SSH**连接服务器，运行如下命令连接数据库
   ```
   docker exec -it superset_db psql -U superset
   ```

2. 在**数据库命令模式下**，运行如下的 SQL 语句后，用户 admin 的密码就被设置为`admin123`。
   ```
   update ab_user set password='pbkdf2:sha256:150000$w8vfDHis$b9c8fa353137417946766ed87cf20510da7e1e3a7b79eef37426330abef552bf' where username='admin';
   ```

