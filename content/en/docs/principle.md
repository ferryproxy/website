---
title: "Technology Principle"
---

# Technology Principle

## Communication and penetration

Ferry-Tunnel uses the capabilities of the ssh protocol for communication and penetration between Ferry-Tunnel

The following capabilities are primarily used
- [direct-tcpip][tcpip]
- [tcpip-forward][tcpip]
- [direct-streamlocal][streamlocal]
- [streamlocal-forward][streamlocal]

[streamlocal]: https://github.com/openssh/openssh-portable/blob/master/PROTOCOL
[tcpip]: https://datatracker.ietf.org/doc/html/rfc4254

There are two core points
- Listen to a local port, connect to the Ferry-Tunnel on the other side, and forward all connections through it
- Connecting to the peer Ferry-Tunnel and listening to a port, and forwarding connections from the listening port to the local

## Service Discovery

Each exported service port will be assigned a port in the Ferry-Tunnel of the imported cluster

Ferry will create a port in the imported cluster for the Headless Service to point to the Ferry-Tunnel's corresponding service in this cluster
