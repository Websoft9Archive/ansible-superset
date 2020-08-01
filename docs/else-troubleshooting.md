# Troubleshooting

We collect the most common troubleshooting of using Superset for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`

#### Superset service can't start?

Insufficient disk space and memory, incorrect configuration file may cause the failure to start the service. 

It is recommended to first check through the command.

```shell
# restart Superset service
systemctl status superset
journalctl -u superset

# view disk space
df -lh

# view memory rate
free -lh
```

#### Error in Chrome when modify password?

This error is not attribute to Superset server, once you have upgraded you local Chrome, it solved

![chrome error of Superset](https://libs.websoft9.com/Websoft9/DocsPicture/zh/superset/superset-chromeerror-websoft9.png)
