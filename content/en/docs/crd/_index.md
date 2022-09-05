---
title: "CRD"
---

# CRD

<img src="/images/crd.png" width="800">

[Hub][2] Define a Hub that communicates with other Hubs

[Route][3] Define a routing rules for individual services between hubs

[RoutePolicy][4] Is used to define generic composite routing rules, which will eventually convert to [Route][3]

[ServiceImport/ServiceExport][1] Is for compatibility [mcs api][1], which will eventually convert to  [RoutePolicy][4]

TunnelRule It's the rules for building tunnels, The CRD has not been defined and is stored using ConfigMap

ServicePort  It is to establish a Service/Endpoint for the imported tunnel, The CRD has not been defined and is stored using ConfigMap

[1]: ./mcs_api
[2]: ./hub
[3]: ./route
[4]: ./route_policy