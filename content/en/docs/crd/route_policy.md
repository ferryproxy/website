---
title: "Route Policy"
---

# Route Policy

RoutePolicy is used to define generic composite routing rules, which will eventually convert to [Route CR][1]

## Explicit Route
### One-to-one import

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
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
This is a CR equivalent to the [Route CR][1] example

### Import from multiple Hubs

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
    - hubName: cluster-2
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
```

This routing rule generates two [Route CR][1], 
app-1.default from [Hub][2] cluster-1 and cluster-2 into [Hub][2] cluster-0, respectively. 
This is done by configuring multiple backends at the endpoint of cluster-0's app-1.default to point to the two imported routes

Even if it is written in a different RoutePolicy CR or [Route CR][1], multiple backends will be configured for the endpoint as long as the import destinations are the same

### Exporting to multiple Hubs

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
    - hubName: cluster-2
      service:
        namespace: default
        name: app-1
```

This rule is actually equivalent to two one-to-one rules

## Macth Route

In addition to explicit routing, Ferry provides the ability to filter the imported and exported services by label
However, it is important to note that matching routes cannot modify the imported name

### Bulk export using Label filtering
``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        labels:
          export: enabled
        namespace: default
  imports:
    - hubName: cluster-0
```

This routing rule will match all services with `export=enabled` label in namespace default of [Hub][2] cluster-1 for export to [Hub][2] cluster-0

### Bulk import using Label filtering
``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        labels:
          export: enabled
        namespace: default
  imports:
    - hubName: cluster-0
      service:
        labels:
          export-2: enabled
```

This rule adds to the previous one that the exported service must also have the `export-2=enabled` label

[1]: ./route
[2]: ./hub