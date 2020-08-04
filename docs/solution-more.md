# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Database dependencies

Superset does not ship bundled with connectivity to databases, except for Sqlite, which is part of the Python standard library. You’ll need to install the required packages for the database you want to use as your metadata database as well as the packages needed to connect to the databases you want to access through Superset.

[Here](https://superset.incubator.apache.org/installation.html?highlight=pip%20install%20mysqlclient#database-dependencies)’s a list of some of the recommended packages.

Examples:    

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


## Domain binding

The precondition for binding a domain is that Superset can accessed by domain name.

Nonetheless, from the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

Superset domain name binding steps:

1. Connect your Cloud Server
2. Modify [Nginx vhost configuration file](/stack-components.md#nginx), change the **server_name**'s value to your domain name
   ```text
   server
   {
   listen 80;
   server_name www.example.com;  # 此处修改为你的域名
   ...
   }
   ```
