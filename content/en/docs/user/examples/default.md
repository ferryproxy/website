---
title: "Default Example"
---

# Default Example

{{< hint info >}}
Prepare at least two clusters for demonstration 

Can be a cluster of one node or a cluster of Kind but at least two.
{{< /hint >}}

<img src="/images/cloud-to-cloud.png" width="600">

## Download ferryctl

ferryctl is the installation and operation tool for ferry 

A ferryctl needs to be installed for each cluster's control node 

https://github.com/ferryproxy/ferry/releases

## Initialize Control Plane Cluster


``` bash
# execute on control plane
ferryctl control-plane init
```

## Join a Data Plane Cluster

3 steps are required to configure

### Define which Data Plane Cluster needs to be joined

``` bash
# execute on Control Plane Cluster
ferryctl control-plane join cluster-1
```

### Execute on the Data Plane Cluster

After the last command is executed of Control Plane Cluster, it responds with a command, copied to Data Plane Cluster to run.

### Execute on the Control Plane Cluster

After the last command is executed of Data Plane Cluster, it responds with a command, copied to the Control Plane Cluster to run.

## Quickly pull up a test environment locally

Requirement: Docker, Kind, Go

``` bash
git clone https://github.com/ferryproxy/ferry
go install ./cmd/ferryctl
./test/hack/start-environment.sh default
```

Two clusters will be started using Kind, and the ferry-controller will be installed in the Control Plane Cluster, but no routing rules will be configured

[Environment](https://github.com/ferryproxy/ferry/blob/main/test/environments/default/)

Configuration route rules

``` yaml
# Map cluster-1's web-1.test.svc to control-plane's web-1.test.svc
# Map control-plane's web-0.test.svc to cluster-1's web-0.test.svc
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
metadata:
  name: ferry-test
  namespace: ferry-system
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: test
        name: web-1
    - hubName: control-plane
      service:
        namespace: default
        name: web-0
  imports:
    - hubName: cluster-1
    - hubName: control-plane
```

[Sample](https://github.com/ferryproxy/ferry/blob/main/test/test/test-in-both.sh)