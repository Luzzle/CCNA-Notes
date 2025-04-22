#ccna-day19

### Overview
DTP is a Cisco protocol that allows cisco devices to dynamically determine their interface status (access or trunk) without manual configuration.

```ios
# switchport mode dynamic ?
auto:
- switchport will only form a trunk if the switch connected to it is actively trying to form a trunk. only in modes mode trunk or dynamic desirable.

desirable:
- switchport will actively try to form a trunk. It will form a trunk if connected to another switch in the mode trunk, dynamic desirable, dynamic auto
```

You can disable DTP negotiation with `switchport negotiate`

### dot1q or ISL
DTP can negotiate if they are using ISL or dot1q for encapsulation. 
DTP frames are sent in VLAN1 if using ISL or native VLAN if sent in dot1q.