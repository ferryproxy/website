---
title: "Home"
---

# Ferry Proxy

Ferry is a Kubernetes multi-cluster communication component that eliminates communication differences between clusters as if they were in a single cluster, regardless of the network environment those clusters are in.

The main idea of Ferry is to map a Service from one cluster to another cluster, and applications in the other cluster just need to access the Service normally.

The Tunnel component of the Ferry project is mainly used to bridge the communication between different clusters and has no requirements on the network environment and network segment currently used by the cluster.

## Public to Public

<img src="/images/cloud-to-cloud.png" width="600">

[Quick Start](./docs/user/examples/default)

## Public to Private

<img src="/images/cloud-to-edge.png" width="600">

[Quick Start](./docs/user/examples/data-plane-unreachable)

## Private to Public

<img src="/images/edge-to-cloud.png" width="600">

[Quick Start](./docs/user/examples/control-plane-unreachable)

## Private to Private

<img src="/images/edge-to-edge.png" width="800">


## Example

Ferry defines a very simple API for configuring the rules for mapping Services between clusters

It is very simple to describe which services need to be exposed to other clusters

<img src="/images/case.png" width="600">

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
metadata:
  name: ferry-rule
  namespace: ferry-system
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
```
