#ccna-day28

## Overview
You can configure the OSPF network type on an interface with `ip ospf network [type]`. 

### Broadcast
Enabled by default on **[[Ethernet]]** and **FDDI (Fiber Distributed Data Interfaces)** interfaces.
Routers *dynamically discover* neighbors by sending and receiving hello packets using multi cast 224.0.0.5.

A **DR (designated router)** and **BDR (Backup designated router)** must be elected on each subnet (or only a DR if there are no neighbors).
Routers that are neither become **DROther**.

##### DR Election Policy
1) Highest OSPF interface priority
2) Highest OSPF RID

In the broadcast network type, routers will only form a full OSPF adjacency with the DR an BDR of the segment.

Therefore routers only exchange LSA's with the DR and BDR. DROthers will not exchange LSAs with each other.

### Point-to-point
Enabled by default on **PPP (Point-to-point Protocol**) and **HDLC (High Level Data Link)** interfaces. Primarily this is enabled on [[Serial Interfaces]].

No DR and BDR are elected, and both routers will form a full adjacency with each other.
### Non-broadcast
Enabled by default on **Frame Relay** and **X.25** interfaces.