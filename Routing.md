#ccna-day11

### Overview
Routing is the process routers use to determine the path that an IP packet should take to reach their destination.

Routers store all of their known destinations in a routing table.

There are 2 main routing methods routers use to learn routes:
- **Dynamic Routing**: Routers use dynamic routing protocols (i.e. OSPF) to share routing information with each other automatically.

- **Static Routing**: A network engineer manually configures routes on the routers.

A packet destined to its own router will match both Connected and Local routes. It will choose the most specific route.

If the router does not have a route to the destination, it will drop the packet.

### Static Routing
Static routing allows a router to forward packets to a network not directly connected to itself.

To configure static routing you must specify the destination network and the next hop towards that network. 

To configure a static route in Cisco IOS: `ip route network-ip-address netmask next-hop`
Alternatively `ip route network-ip-address netmask exit-interface`

A default route is a route to 0.0.0.0/0, meaning the least specific ip address. If the router has no more specific routes that match the destination, it will forward it to the default route.

This is often used to direct traffic to the internet.

To configure a default route: `ip route 0.0.0.0 0.0.0.0 [default-ip or interface]`

