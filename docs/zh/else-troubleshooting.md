# 故障处理

此处收集使用 Superset 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### 如何查看错误日志？

通过 `sudo docker logs superset_postgre_1` 查看 Superset 容器错误日志

#### Superset 运行报错？

先通过如下的命令，重新运行容器

```
cat /data/wwwroot/superset
docker-compose down
docker-compose up -d
```

如果仍然报错，请检查数据库连接、持久化存储挂载是否准确无误。

