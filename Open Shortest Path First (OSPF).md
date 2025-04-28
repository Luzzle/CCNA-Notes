#ccna-day24 

### Overview
**Metric** - Cost
The cost of each link is calculated based on bandwidth. The total metric is the total cost of each link in the route.

Uses Dijkstra's Algorithm to determine the shortest path to destination.

### Cost
Calculated based on the bandwidth (speed) of the interface.
- Reference Bandwidth / Interface Bandwidth
- Default bandwidth is 100 mbps
- Minimum cost of 1

```ios
(config-router)# auto-cost reference-bandwidth megabits-per-second
```

### LSAs and LSBs
Routers store information about the network in LSA's (Link State Advertisements) which are organized in a structure called LSDB (Link State Database).

Routers will flood LSA's until all routers in the OSPF area develop the same map of the network.

##### LSA Flooding
A router will create a LSA to tell its neighbors about networks attached to itself. The LSA is flooded throughout the network until all routers have received it.

This results in all routers sharing the same LSDB.

### OSPF Areas
OSPF uses **areas** to divide up a network.

Larger networks can have performance issues if they are single area.
- more time to calculate routes, needing exponentially more time.
- takes up more memory on the routers
- any small change causes every router to flood LSAs and run the SPF algorithm again.

The backbone area (area 0) is an area that all other areas must connect to.
Routers with all interfaces in the same area are called **internal routers**, whilst others in multiple areas are called **Area Border Routers (ARBs)**
###### ARBs
- ARBs maintain a separate LSDB for each area they are connected to. Each ARB should be connected to at most 2 areas.

An **intra-area** route is a route to a destination inside the same OSPF area.
An **inter-area** route  is a route to a different OSPF area.

### Configuration
```ios
(config)# router ospf [Process ID] -- Process ID is locally significant
(config-router)# network [network address] [wildcard subnet] area [num]
```

An **autonomous system boundary router** is an OSPF router that connects the OSPF network to an external network.


