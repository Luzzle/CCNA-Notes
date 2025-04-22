#ccna-day23

### Overview
EtherChannel groups multiple interfaces together to act as a single interface.
[[Spanning Tree Protocol (STP)|STP]] will treat this group as a single interface, traffic using EtherChannel will be load balanced among the physical interfaces in the group.

### Flows
EtherChannel balances based on flows. A flow is a communication between 2 nodes in the network.
Frames in the same flow will be forwarded using the same physical interface to avoid arriving out of order.


### Configuration
#### PAgP (Port Aggregation Protocol)
- Cisco proprietary
- Dynamically negotiates the creation/maintenance of the EtherChannel.

#### LACP (Link Aggregation Control Protocol)
- Industry standard (802.3ad)

#### Static EtherChannel
- No protocol is used to dynamically determine if an EtherChannel should be formed.
- Interfaces are statically configured.

```ios
# (config-if) channel-group 1 mode ?
active           Enable LACP unconditionally
auto             Enable PAgP only if a PAgP device is detected
desirable        Enable PAgP unconditionally
on               Enable Etherchannel only
passive          Enable LACP only if a LACP device is detected
```

The channel group number has to match for interfaces on the same switch, not on the other switch.

```ios
# show etherchannel summary

P - bundled in port-channel
S - Layer2
U - in use


# show etherchannel port-channel
- displays information about the virtual port-channel interfaces on the switch

# show spanning-tree

# port-channel load-balance [mode]
- configures the etherchannel load balancing mode on the switch
```