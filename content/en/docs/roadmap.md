# Roadmap

{{< hint info >}}
This document outlines some goals, non-goals, and future aspirations for Ferry as a project.
{{< /hint >}}

## DONE
- [x] Engage encryption
- [x] Use Ferryctl alone to configure service mapping between clusters without the Controller
- [x] Support multi-level proxy

## TODO
- [ ] Support complete uninstallation itself and cleanup
- [ ] Status is monitored and displayed in the status of the Hub
- [ ] Adapting to the ecosystem
- [ ] SSH-via-QUIC: QUIC is used to replace TCP in SSH, no need to reconnect after an IP change, expect better performance
- [ ] Support [mcs api](https://github.com/kubernetes-sigs/mcs-api)
- [ ] Support any server with sshd as a hub without Cluster

## IDEA
- [ ] Multi-cluster failover
- [ ] Multi-cluster load balancing
- [ ] IP-based access control
- [ ] Provide an cluster-to-cluster view of traffic flow and service performance
- [ ] Support UDP of Service
- [ ] Supports direct UDP p2p connection between two clusters without public IPs

## Suggesting

If we've missed something that would make Ferry more useful to you, please let us know.
The best way to do this is to [Submit an Issue](https://github.com/ferryproxy/ferry/issues/new) and include information about how you plan to use Ferry.
