# 路线图

{{< hint info >}}
本文概述了Ferry作为一个项目的一些目标、非目标和未来的期望。
{{< /hint >}}

## DONE
- [x] 通信加密
- [x] 只使用 Ferryctl 来配置集群之间的服务映射，而不使用 Controller
- [x] 支持多级代理
- [x] 支持 [mcs api](https://github.com/kubernetes-sigs/mcs-api)
- [x] 负载均衡
- [x] 监控状态，并显示在Hub的状态中

## TODO
- [ ] 支持完整的卸载自身和清理
- [ ] 适配上下游生态
- [ ] 单个 Hub 支持多副本 Tunnel
- [ ] SSH-via-QUIC: Tunnel 之间的 ssh 协议使用 quic 替换 tcp, 在 IP 变化后无需重新连接, 预期更好的性能
- [ ] 支持任何设备主动连接并加入作为 Hub, 提供 SDK 和 Binary
- [ ] 支持两个无公网 IP 的 Hub 经过控制面撮合, 通过 UDP p2p 直连
- [ ] 故障转移
- [ ] 就近访问

## IDEA
- [ ] 提供流量和业务性能的视图
- [ ] 支持 Service 的 UDP

## Suggesting

如果我们遗漏了一些东西，让 Ferry 对你更有用，请让我们知道。
最好的方法是 [提交一个 Issue](https://github.com/ferryproxy/ferry/issues/new)，并包括关于你打算如何使用 Ferry 的信息。
