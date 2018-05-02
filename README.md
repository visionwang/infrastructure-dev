# 介绍
这是帮助你快速启动Spring Cloud开发环境的docker配置仓库.

这个环境包括如下服务：

- Mongo DB 3.4.10
- Redis 3.2
- RabbitMQ 3.6 with `stomp` and `shovel` plugins
- Spring Cloud 
  - config-server
  - eureka-server

## 使用前提 
1. 安装[Docker 17+](https://www.docker.com)
2. 安装[Docker Compose](https://docs.docker.com/compose/install/#prerequisites)
3. 在`.env`里配置config-server的文件仓库

## 使用方式
### 启动 `docker-compose up -d`
 eureka-server需要依赖config-server的成功启动，所以**eureka-server需要等待一段时间后才能正常启动**。

### 销毁环境 `docker-compose down`

### 查看服务运行情况参考`docker-compose help`
	
## 运行数据
默认情况下,环境销毁后数据会丢失，使用下面的方法可以把数据保存在本地

```
docker volume create --opt type=none --opt device=<absolute path of host> --opt o=bind --name mongo_data
```
Update `docker-compose.yml` as below,
```
volumes:
  redis_data:
  mongo_data:
    external: true
```
