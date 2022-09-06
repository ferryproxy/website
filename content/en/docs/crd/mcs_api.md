---
title: "MCS API"
---

# MCS API

This is the set of APIs defined in [kubernetes-sigs/mcs-api][1

Ferry will get the ServiceExport and ServiceImport CRs from all [Hub CRs][3] clusters that have the `mcs.traffic.ferryproxy.io/service=enabled` label.
Get their ServiceExport and ServiceImport CRs, convert them to [RoutePolicy CR][2], so that they are compatible with the mcs api

[1]: https://github.com/kubernetes-sigs/mcs-api
[2]: ./route_policy
[3]: ./hub
