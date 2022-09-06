---
title: "Hub"
---

# Hub

Hub CR defines a Hub, which is the address to communicate with other Hubs,
For now only one cluster is supported, in the future it will be added to support any possible device as a Hub, even your laptop

Hub provides the basis for [RoutePolicy CR][1] and [Route CR][2] calculations

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: Hub
spec:
  gateway:
    # Reachable indicates that this Hub is reachable
    reachable: true

    # Address is the address of this Hub, used when Reachable is true
    address: 1.1.1.1:31087

    # NavigationWay is a list of Hub names through which this Hub needs to reach other Hubs, used when this Hub reaches other Hubs,
    # used by RoutePolicy to calculate Routes
    navigationWay:
      - hubName: hubname

    # ReceptionWay is a list of Hub names through which other hubs needs to reach this Hub,
    # used when other Hubs reaches this Hub and Reachable is true,
    # used by RoutePolicy to calculate Routes
    receptionWay:
      - hubName: hubname

    #  NavigationProxy is a list of proxies through which this Hub to reach other Hubs must need to go through,
    # used when this Hub reaches other Hubs
    navigationProxy:
      - proxy: hubname

    # ReceptionProxy is a list of proxies through which other Hubs to reach this Hub must need to go through,
    # used when other Hubs reaches this Hub and Reachable is true
    receptionProxy:
      - proxy: hubname

```

[1]: ./route_policy
[2]: ./hub
