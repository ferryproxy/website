---
title: "MCS API"
---

# MCS API

这是在 [kubernetes-sigs/mcs-api][1] 定义的一套 API

Ferry 会从所有 [Hub CR][3] 被加上 `mcs.traffic.ferryproxy.io/service=enabled` label 的集群中
获取其 ServiceExport 和 ServiceImport 的 CR, 将其转换为 [RoutePolicy CR][2], 以此兼容 mcs api

[1]: https://github.com/kubernetes-sigs/mcs-api
[2]: ./route_policy
[3]: ./hub
