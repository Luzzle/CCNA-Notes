#ccna-day18

### Overview

- A multilayer switch is capable of both switching and routing.
- A layer 3 switch is layer 3 aware. IP addresses can be assigned to interface, which can be used as routed ports.
- It is also capable of creating virtual interfaces with their own IP addresses.
- It can be used for inter-[[VLAN|vlan]] routing.

 A multilayer switch is better than trunking for large networks, as trunking can cause network congestion into the router.

### Switch Virtual Interfaces (SVI)
- SVI's are the virtual interfaces you assign IP addresses in a multilayer switch
- Configure each PC to use the SVI as their gateway address
- For traffic destined outside the lan, setup an ip address and a default route on its connection to a router bordering the LAN.

### Configuration
```ios
# ip routing enables layer 3 routing on the switch
# interface [number]
# no switchport
# ip address [ip] [subnet]
```

*Configure SVI*
```ios
# interface [vlan]
# ip address [ip] [subnet]
# no shutdown
```

Conditions for VLAN to be up
- VLAN must exist on the switch
- Switch have at least one access port in the VLAN in an up/up state and/or one trunk port up/up
- The VLAN must not be shutdown
- The SVI must be up
