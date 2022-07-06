---
title: "Quick Start"
---

# Quick Start
{{< hint info >}}
Prepare at least two clusters for demonstration 

Can be a cluster of one node or a cluster of Kind but at least two.
{{< /hint >}}

## Download ferryctl

ferryctl is the installation and operation tool for ferry 

A ferryctl needs to be installed for each cluster's control node 

https://github.com/ferry-proxy/ferry/releases

## Initialize control plane


``` bash
# execute on control plane
ferryctl control-plane init
```

## Declares to the control plane which data plane needs to join 

``` bash
# execute on control plane to pre-join other data plane
ferryctl control-plane pre-join direct cluster-1
```

If the network environment is more complex, please refer to [Join Mode](../join-mode)

## Data plane is ready to be managed by control plane 

After the last command is executed of control plane, it responds with a command, copied to data plane to run.

## Control plane begins to control data plane

After the last command is executed of data plane, it responds with a command, copied to the control plane to run.

## Configuration rules

The test application needs to deploy and configure the Service 

Rules for configuring Ferry on the control plane cluster

``` yaml
# Mapping app-1.default.svc of cluster-1 to the app-1.default.svc of control-plane
apiVersion: ferry.zsm.io/v1alpha1
kind: FerryPolicy
metadata:
  name: ferry-rule
  namespace: ferry-system
spec:
  rules:
    - exports:
        - clusterName: cluster-1
          match:
            namespace: default
            name: app-1
      imports:
        - clusterName: control-plane
          match:
            namespace: default
            name: app-1
```

