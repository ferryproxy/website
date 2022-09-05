# Roadmap

{{< hint info >}}
This document outlines some goals, non-goals, and future aspirations for Ferry as a project.
{{< /hint >}}

## DONE
- [x] Engage encryption
- [x] Use Ferryctl alone to configure service mapping between clusters without the Controller
- [x] Support multi-level proxy
- [x] Support for [mcs api](https://github.com/kubernetes-sigs/mcs-api)
- [x] Load balancing

## TODO
- [ ] Support complete uninstallation of itself and cleanup
- [ ] Monitor status and display in Hub's status
- [ ] Adapting to the ecosystem
- [ ] Multi-replicas tunnels for a single Hub
- [ ] SSH-via-QUIC: QUIC is used to replace TCP in SSH, no need to reconnect after an IP change, expect better performance
- [ ] Support for any device to actively connect and join as a hub, SDK and Binary provided
- [ ] Support for two hubs without public IPs to connect directly via UDP p2p after control plane collocation
- [ ] Failover
- [ ] Proximity access
- [ ] Access control

## IDEA
- [ ] Provide an view of traffic flow and service performance
- [ ] Support UDP of Service

## Suggesting

If we've missed something that would make Ferry more useful to you, please let us know.
The best way to do this is to [Submit an Issue](https://github.com/ferryproxy/ferry/issues/new) and include information about how you plan to use Ferry.
