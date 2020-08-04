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

Superset 配置文件 [superset_config.py](https://superset.incubator.apache.org/installation.html?highlight=smtp#configuration) 是自定义配置 Superset 功能的主要入口。

## 安装数据库驱动

虽然 Superset 默认支持数十种数据库的分析，但除了SQLite（它是Python标准库的一部分）外，Superset 默认并没有默认安装所有数据库的驱动（连接程序）。  

范例：  

```
sudo docker exec -it superset_postgre_1 bash

# MySQL
pip install mysqlclient

# PostgreSQL
pip install psycopg2	

# Hive
pip install pyhive

#Redshift
pip install sqlalchemy-redshift
```

参考官方[Database dependencies](https://superset.incubator.apache.org/installation.html?highlight=pip%20install%20mysqlclient#database-dependencies)


