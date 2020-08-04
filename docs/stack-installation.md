# Initial Installation

If you have completed the Superset deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the **TCP:80** is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for Superset

## Superset Installation Wizard

1. Using local Chrome or Firefox to visit the URL *http://DNS* or *http://Internet IP*, enter login page of Superset
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-login-websoft9.png)

2. Log in to Superset web console([Don't have password?](/stack-accounts.md#superset))  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-console-websoft9.png)

3. Set you new password from: 【Super Admin】>【Profile】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/superset/superset-resetpw-websoft9.png)

> More useful Superset guide, please refer to [Getting Started with Superset using Docker](https://github.com/apache/incubator-superset/blob/master/docker/README.md)

## Q&A

#### I can't visit the start page of Superset?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### What's installation method for Superset?

Based on Docker installation