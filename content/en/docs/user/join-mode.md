---
title: "Join Mode"
---

# Join Mode

There are currently two ways to join

1. direct
2. tunnel

## direct

It is suitable for the case where the network between clusters is interoperable,
and there is no need to do penetration or proxy operations.


## tunnel

Applicable to the situation where the control plane cluster cannot access the data plane cluster but the data plane cluster can access the control plane cluster.
At this time, it is necessary to establish intranet penetration from the control plane cluster to the data plane cluster. 
