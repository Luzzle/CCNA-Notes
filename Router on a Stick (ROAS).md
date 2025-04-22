#ccna-day17 

### Overview
Divides a single interface on a router to several sub interfaces for inter-VLAN routing.
![[Pasted image 20250411063500.png]]

The router interface is configured with a VLAN tag and IP Address on each sub-interface
The router will behave as if frames arriving with a certain VLAN tag will have arrived on the sub-interface configured with that VLAN tag.

```ios
# interface [number]

# interface [subinterface]
# encapsulation dot1q [vlan]
# ip address [ip] [subnet]

... repeat for each subinterface
```
