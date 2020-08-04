# SMTP

Sending mail is a common feature for Superset. After a large number of user practice feedback, only one way is recommended, that is, using the **third-party STMP service** to send the email.

> Do not try to install **Sendmail** or other Mail server software on your Cloud Server for sending mail, because it is very difficulty in maintenance.

Follow is the sample using **SendGrid's SMTP Service** to configure sending mail:

1. Log in SendGrid console, prepare your SMTP settings like the follow sample
   ```
   SMTP host: smtp.sendgrid.net
   SMTP port: 25 or 587 for unencrypted/TLS email, 465 for SSL-encrypted email
   SMTP Authentication: must be checked
   SMTP Encryption: must SSL
   SMTP username: websoft9smtp
   SMTP password: #fdfwwBJ8f    
   ```
2. Edit [Superset configuration file](/stack-components.md#superset)([refer to docs](https://superset.incubator.apache.org/installation.html?highlight=smtp)）
   ```
   # smtp server configuration
   EMAIL_NOTIFICATIONS = True  # all the emails are sent using dryrun
   SMTP_HOST = 'smtp.163.com'
   SMTP_STARTTLS = True
   SMTP_SSL = True
   SMTP_USER = 'websoft9@163.com'
   SMTP_PORT = 465
   SMTP_PASSWORD = '#wwBJ8'
   SMTP_MAIL_FROM = 'websoft9@163.com'
   ```
3. Saved and restart Superset container
   ```
   sudo docker restart superset_postgre_1
   ```

More SMTP Service(Gmail, Hotmail, QQ mail, Yahoo mail, SendGrid and so on)  settings or Issues with SMTP, please refer to Websoft9's *[SMTP Guide](https://support.websoft9.com/docs/faq/tech-smtp.html)*
