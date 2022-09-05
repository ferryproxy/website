---
title: "Route"
---

# Route

Route CR Define a routing rules for individual services between hubs

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: Route
spec:
  export:
    hubName: cluster-1
    service:
      namespace: default
      name: app-1
  import:
    hubName: cluster-0
    service:
      namespace: default
      name: app-1
```

The example CR describes Hub cluster-1 exporting Service app-1.default, importing it in Hub cluster-0 and naming it app-1.default
The name and namespace of the import and export do not have to be the same
