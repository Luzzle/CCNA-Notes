#ccna-day36
### Overview
LLDP is an industry standard protocol (IEEE 802.1AB).
Usually disabled by default on Cisco platforms.

LLDP messages are periodically sent to multicast [[MAC address]] `0180.C200.000E`.

Default timers:
- Sent every 30 seconds
- Held for 120 seconds
- Reinitialization delay timer is set to 2 seconds by default, this timer delays the actual initialization of LLDP.

### Configuration
```ios
(config)# lldp run
(config-if)# lldp transmit - enable on specific interface
(config-if)# lddp receive
(config)# lldp timer SECONDS
(config)# lldp holdtime SECONDS
(config)# lldp reinit SECONDS
```

```ios
# show lldp
# show lldp traffic
# show lldp interface
# show lldp neighbors
# show lldp entry NAME
```