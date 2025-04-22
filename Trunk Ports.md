#ccna-day17

### Overview
Trunk ports can be used to carry traffic from multiple VLAN's over a single interface.

```ios
# interface [number]
# switchport trunk encapsulation dot1q
# switchport mode trunk
# switchport trunk allowed vlan [add|remove|all|none|except OR list vlans allowed]
```

```ios
# show interfaces trunk
```

