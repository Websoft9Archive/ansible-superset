# 初始化安装

在云服务器上部署 Superset 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:80** 端口是否开启
3. 若想用域名访问 Superset，请先到 **域名控制台** 完成一个域名解析

## Superset 安装向导

1. 使用本地电脑的 Chrome 或 Firefox 浏览器访问网址：*http://域名* 或 *http://服务器公网IP*, 进入登录页面
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-login-websoft9.png)

2. 输入账号密码（[不知道账号密码？](/zh/stack-accounts.md#superset)），成功登录到 Superset 后台  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-console-websoft9.png)

3. 修改密码：【Superset Admin】>【Profiles】>【Reset my Password】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-resetpw-websoft9.png)

4. 修改语言：通过右上角国旗图标设置你所需的语言 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-setlanguagech-websoft9.png)
   
   > 在0.999及以上的版本中，Superset取消了菜单栏的语言设置，须通过修改配置文件进行语言设置，方法如下:
   > 1. 进入Superset容器：docker exec -it -u root superset_app bash  
   > 2. 安装 vim 编辑器：apt-get update && apt-get install vim 
   > 3. 编辑配置文件：vim superset/config.py  
   > 4. 找到本地化配置项，将值设为 zh ，切换为中文环境：BABEL_DEFAULT_LOCALE = 'zh'  
   > 5. Ctrl + D 退出容器，并重启容器：docker restart superset_app
   > 6. 重新打开Superset，查看中文界面
  

## Superset 入门向导

下面以连接 Superset 从 MySQL 数据源中获取数据进行分析作为范例：

1. 登录后，依次打开：【Data】>【Databases】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-database-websoft9.png)

2. 点击右上角【数据库】，输入要连接的数据地址、端口、库名以及驱动（[参考](https://docs.sqlalchemy.org/en/13/core/engines.html)）  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-connect-websoft9.png)

3. 点击【确认】，追加的数据库显示在列表中
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-connect-websoft9.png)

4. 依次打开菜单栏：【Data】>【Datesets】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-dataset-websoft9.png)

5. 点击追加Datasets，依次选择库、SCHEMA、Table，点击追加
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-selecttable-websoft9.png)

6. 新追加的表已经显示在Datasets一览了
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-datalist-websoft9.png)

> 需要了解更多 Superset 的使用，请参考官方文档：[Superset documentation](https://superset.apache.org/docs/intro)

## 常见问题

#### 浏览器打开IP地址，无法访问 Superset（白屏没有结果）？

您的服务器对应的安全组 80 端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### Superset 采用的哪种安装方式？

本项目基于 Docker 安装
