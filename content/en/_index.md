---
title: "Home"
---

# Ferry Proxy

Ferry is a Kubernetes multi-cluster communication component that eliminates communication differences between clusters as if they were within a cluster, regardless of the network environment those clusters are in.

The main idea of Ferry is to map the Service of one cluster to another cluster, and the application of the other cluster only needs to access the Service normally.

The Tunnel component in the Ferry project is mainly used to open up communication between different clusters, and has no requirements for the network environment and network segment currently used by the cluster.

## Public to Public

<img src="/images/cloud-to-cloud.png" width="600">

## Public to Private

<img src="/images/cloud-to-edge.png" width="600">

## Private to Public

<img src="/images/edge-to-cloud.png" width="600">

## Private to Private

<img src="/images/edge-to-edge.png" width="800">


## Example

Ferry defines a very simple API for configuring service mapping rules between clusters

It can be very simple to describe which services need to be exposed to other clusters

<img src="/images/case.png" width="800">

## How to use ferry

See the [Quick Start](./docs/user/quick-start)
