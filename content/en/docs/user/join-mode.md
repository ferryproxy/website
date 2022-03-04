---
title: "Join Mode"
---

# Join Mode

``` console
> ferryctl control-plane pre-join --help
Generate command for data plane join
Need to copy the generated command to run on the data plane.

Usage:
  ferryctl control-plane pre-join [command]

Aliases:
  pre-join, p, pj, join, j

Available Commands:
  direct      Clusters can reach each other
  tunnel      Control plane can't touch the data plane

Flags:
  -h, --help                                  help for pre-join
```
There are currently two ways to join

1. direct
2. tunnel

## direct

It is suitable for the case where the network between clusters is interoperable,
and there is no need to do penetration or proxy operations.


## tunnel

Applicable to the situation where the control plane cluster cannot access the data plane cluster but the data plane cluster can access the control plane cluster.
At this time, it is necessary to establish intranet penetration from the control plane cluster to the data plane cluster. 
