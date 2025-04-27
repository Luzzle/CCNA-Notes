#ccna-day24 #ccna-day25

*see [[Wildcard Masks]]*
### Overview
**Metric** - Calculation based on bandwidth and delay.
Complex formula that can take into account many values. By default the bandwidth of the slowest link and the total delay of all links in the route are used.

Faster than [[Routing Information Protocol (RIP)|RIP]] in reacting to changes in the network.
Sends messages using multi-cast address 224.0.0.10



### Configuration
```ios
(config)# router eigrp 1
(config-router)# no auto-summary
(config-router)# passive-interface g2/0
(config-router)# network 10.0.0.0
(config-router)# network 172.16.1.0 0.0.0.15
```

The Autonomous System (AS) number must match or they will not form an adjacency and share router interface.
The network command assumes a classful address unless a mask is specified.

*The **passive interface** neither originates EIGRP packets nor processes them. But the network to which the passive interface non passive is connected will be advertised throughout the routed domain.*
### Router ID
Router ID order of priority
1) Manual configuration
2) Highest IP address on a loopback interface
3) Highest IP address on a physical interface

```ios
(config-router)# eigrp router-id [IP]
```

