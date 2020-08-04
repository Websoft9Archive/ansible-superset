# Troubleshooting

We collect the most common troubleshooting of using Superset for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs of Superset

```
sudo docker logs superset_postgre_1
```

#### Superset error?

It is recommended to first check through the command.

```shell
cat /data/wwwroot/superset
docker-compose down
docker-compose up -d
```