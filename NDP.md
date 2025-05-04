#ccna-day33

*see [[IPv6]]*
### Overview
**Neighbor Discovery Protocol** is a protocol used with IPv6 with various functions, particularly replacing [[ARP]].

The [[ARP]] like functionality utilizes ICMPv6 and [[IPv6#Solicited-Node Multicast Address|Solicited-Node Multicast Address]] to learn the MAC address of other hosts.


### NTP Message Types
#### Neighbor Solicitation (NS) - ICMPv6 Type 135
Used to request a MAC address.
Destination IP is a Multicast MAC based on the destination's solicited-node address.

#### Neighbor Advertisement (NA) - ICMPv6 Type 136
Used to respond with the devices MAC address. Equivalent to an ARP reply.

### Router Identification
Another function of NDP allows hosts to automatically discover hosts on a local network.

#### Router Solicitation (RS) - ICMPv6 Type 133
Sent to multicast address FF02::2 (all routers)
Asks all routers to identify themselves.
Sent when an interface is enabled.

#### Router Advertisement (RA) - ICMPv6 134
Sent to multicast address FF02::1 (all nodes)
The router announces its presence, as well as other information about the link.
Messages can either be sent as a response to RS or periodically.

