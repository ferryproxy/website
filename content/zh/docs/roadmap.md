# 路线图

{{< hint info >}}
本文概述了Ferry作为一个项目的一些目标、非目标和未来的期望。
{{< /hint >}}

- [x] 通信加密
- [x] 只使用Ferryctl来配置集群之间的服务映射，而不使用Controller
- [ ] 监控状态，并显示在Hub的状态中
- [ ] 多集群故障转移
- [ ] 多集群负载均衡
- [ ] 基于 IP 的访问控制
- [ ] 提供流量和业务性能的 cluster-to-cluster 视图
- [ ] 适配上游生态
- [ ] 支持 UDP
- [ ] 支持 [mcs api](https://github.com/kubernetes-sigs/mcs-api)
- [ ] 支持两个无公网 IP 的集群通过 UDP p2p 直连
- [ ] 支持任何带有 sshd 的服务器作为 Hub，不需要集群
