---
title: "CRD"
---

# CRD

<img src="/images/crd.png" width="800">

[Hub][2] 定义一个 Hub, 是与其他 Hub 通信地址

[Route][3] 定义 Hub 之间的单个 Service 的路由规则

[RoutePolicy][4] 是用于定义通用的复合型的路由规则, 最终会转换成 [Route][3]

[ServiceImport/ServiceExport][1] 是为了兼容 [mcs api][1], 最终会转换成 [RoutePolicy][4]

TunnelRule 是建立隧道的规则, 还未定义CRD, 使用 ConfigMap 存的

ServicePort 是为导入的隧道建立对应的 Service/Endpoint, 还未定义CRD, 使用 ConfigMap 存的

[1]: ./mcs_api
[2]: ./hub
[3]: ./route
[4]: ./route_policy