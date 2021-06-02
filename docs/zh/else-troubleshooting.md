# 故障处理

此处收集使用 Superset 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### 如何查看错误日志？

通过 `sudo docker logs superset_app` 查看 Superset 容器错误日志

#### Superset 运行报错？

先通过如下的命令，重新运行容器

```
cat /data/wwwroot/superset
docker-compose down
docker-compose up -d
```

如果仍然报错，请检查数据库连接、持久化存储挂载是否准确无误。

#### Superset 容器中安装数据库驱动报错？

错误信息：ERROR: Could not install packages due to an OSError: [Errno 13] Permission denied: '/home/superset'
Check the permissions.  

问题原因：权限不足  

解决方案：以 root 用户进入容器 `docker exec -it --user root superset_app bash`，然后再安装驱动  

#### Superset 密码正确，但仍然登录失败？

问题描述：用户名和密码完全正确，但 Superset 仍然登录失败，错误信息 Invalid login, Please try again  
问题原因：暂时未知  
解决方案：重启所有 Superset 容器 `cd /data/wwwroot/superset && docker-compose restart`  