#ccna-day24 

### Overview
**Metric** - Hop count
- Each router in the path counts as one hop. The total metric is the total number of hops to the destination. Considers links of all speeds as equal.

- The maximum hop count is 15 (anything more than that is considered unreachable)

### Messages
**Request**: Ask RIP-enabled neighbor routers to send their routing table.
**Response**: To send the local router's routing table to neighboring routers.

**RIP v1** - Only advertises classful interfaces.
**RIP v2** - Supports VLSM, CIDR, messages are multicast to 224.0.0.9

### Configuration
```ios
(config)# router rip
(config-router)# version 2
(config-router)# no auto-summary 
   - stops converting advertised networks to classful networks.
```

The **network** command tells the router to:
- look for interfaces with an IP address that is in the specified range
- active RIP on the interfaces that fall in that range

Because the network command is [[IPv4#Classes|classful]] 10.0.0.0 is assumed to be 10.0.0.0/8. 
![[Pasted image 20250425062213.png]]
10.0.12.1 and 10.0.13.1 both match, so RIP is activated on both G0/0 and G1/0.
R1 advertises 10.0.12.0/30 and 10.0.13.0/30 to its neighbors.

The network command doesn't tell us the router which networks to advertise, it tells the router which interfaces to activate RIP on, and then the router will advertise the network prefix of those interfaces.

The router will then form adjacencies with its RIP neighbors on those interfaces.

```ios
(config-router)# passive-interface g2/0
```

The passive interface command tells the router to stop sending RIP advertisements out of the specified interface (G2/0)

```ios
(config-router)# default-information originate
```

Advertises the default route. RIP load balances across interfaces as it does not consider speed only hop count.
