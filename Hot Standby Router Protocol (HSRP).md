#ccna-day29 

### Overview
An active and standby router are elected.

Multicast IPv4 address:
- v1: 224.0.0.2
- v2: 224.0.0.102

Virtual MAC: 
- v1: 0000.0c07.acXX (XX - group number)
- v2: 0000.0c9f.fXXX (XXX - group number)

In a situation with multiple subnets / vlans, you can configure a different active router in each subnet / vlan to load balance.

### Configuration
Active router
```ios
# interface [interface]
# standby version 2
# standby [group number] ip [IP] - configure virtual IP
# standby [group number] priority [priority] - highest priority becomes active router
# standby 1 preempt - see First Hop Redundancy Protocols
```
