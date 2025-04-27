#ccna-day24 

### Distance Vector Protocols

- Distance vector protocols operate by sending the following to their directly connected neighbors.
	- their known destination networks
	- their metric to reach their known destination networks
- Router doesn't know about the network beyond its neighbors.

[[Routing Information Protocol (RIP)]]
[[Enhanced Interior Gateway Routing Protocol (EIGRP)]]

### Link State

- When using a link state routing protocol, every router creates a connectivity map of the network.
- To allow this, each router advertises information about its interfaces to its neighbors.
- These advertisements are passed along to other routers, until all routers develop the same map of the network.
- Each router uses this map to calculate the best routes to each destination.

[[Open Shortest Path First (OSPF)]]
[[Intermediate System to Intermediate System (IS-IS)]]

### Administrative Distance
In rare cases where a company uses 2 IGP's, the Administrative Distance is used to determine which routing protocol is preferred.

*See [[Dynamic Routing#Floating Static Routes|Floating Static Routes]]*

| Route protocol / type | AD  |
| --------------------- | --- |
| Directly connected    | 0   |
| Static                | 1   |
| External BGP (eBGP)   | 20  |
| EIGRP                 | 90  |
| IGRP                  | 100 |
| OSPF                  | 110 |
| IS-IS                 | 115 |
| RIP                   | 120 |
| EIGRP                 | 170 |
| Internal BGP (iBGP)   | 200 |
| Unusable route        | 255 |

