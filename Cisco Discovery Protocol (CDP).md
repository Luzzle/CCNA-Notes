#ccna-day36 

### Overview
CDP is a Cisco proprietary protocol enabled on Cisco devices by default.
CDP messages are periodically sent to multicast [[MAC address]] `0100.0CCC.CCCC`

Default timers:
- Sent every 60 seconds
- Information held for 180 seconds

When a device receives a CDP message, it processes and discards the message.

### Configuration
```ios
#show cdp - global cdp information
#show cdp traffic
#show cdp interface
#show cdp neighbors

(config)#cdp run - enable cdp globally
(config-if)#cdp enable - enable on an interface
(config)#cdp timer SECONDS - cdp timer
(config)#cdp holdtime SECONDS - cdp holdtime
(config)#cdp advertise-v2 - enable v2
```