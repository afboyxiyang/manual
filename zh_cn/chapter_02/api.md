---
refcn: chapter_02/api
refen: configuration/api
---

# 远程控制

V2Ray 中可以开放一些 API 以便远程调用。这些 API 都基于 [gRPC](https://grpc.io/)。

当远程控制开启时，V2Ray 会自建一个出站代理，以 `tag` 配置的值为标识。用户必须手动将所有的 gRPC 入站连接通过 [路由](03_routing.md) 指向这一出站代理。

## ApiObject

`ApiObject` 对应配置文件中的 `api` 项。

```json
{
    "tag": "api",
    "services": [
        "HandlerService",
        "LoggerService",
        "StatsService"
    ]
}
```

> `tag`: string

出站代理标识

> `services`: \[string\]

开启的 API 列表，可选的值见 [API 列表](#api-list)。

## 支持的 API 列表 {#api-list}

### HandlerService

一些对于入站出站代理进行修改的 API，可用的功能如下：

* 添加一个新的入站代理；
* 添加一个新的出站代理；
* 删除一个现有的入站代理；
* 删除一个现有的出站代理；
* 在一个入站代理中添加一个用户（仅支持 VMess）；
* 在一个入站代理中删除一个用户（仅支持 VMess）；

### LoggerService

支持对内置 Logger 的重启，可配合 logrotate 进行一些对日志文件的操作。

### StatsService

内置的数据统计服务，详见 [统计信息](stats.md)。
