# Initial Installation

If you have completed the Superset deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the **TCP:80** is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for Superset

## Superset Installation Wizard

1. Using local browser to access URL *http://DNS* or *http://Instance's Internet IP*, enter login page
   ![superset login page](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-login-websoft9.png)

2. Log in to Superset web console([Don't have password?](/stack-accounts.md#superset))  
   ![superset login page](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-console-websoft9.png)

3. Modiyf your password by: 【Super Admin】>【Profile】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-resetpw-websoft9.png)

## Superset Usage Wizard

The following is an example of Superset connecting MySQL data source for analysis:

1. Add data source: After logging in Superset, open:【Data】>【Databases】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-database-websoft9.png)

2. Click 【DATABASE】 in the upper right corner, enter the data server address, port, database name and driver to be connected ([More Reference](https://docs.sqlalchemy.org/en/13/core/engines.html)）  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-connect-websoft9.png)
   
   > mysql://username:password@server:port/database name  

3. Click 【ADD】, the added database will be displayed in the list
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-connect-websoft9.png)

4. Add data table(datasets): Open the menu in turn:【Data】>【Datesets】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-dataset-websoft9.png)

5. Click Add Datasets, select datasource, SCHEMA, Table in turn, and click 【ADD】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-selecttable-websoft9.png)

6. The newly added table has been displayed in the Datasets list.
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-datalist-websoft9.png)

7. Data source added successfully 

> More useful Superset guide, please refer to [Superset documentation](https://superset.apache.org/docs/intro)

## Q&A

#### I can't visit the start page of Superset?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### What's installation method for Superset?

Based on Docker installation
