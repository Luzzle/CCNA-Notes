#ccna-day9

### Overview
Switch interfaces do not have the shutdown command applied by default, they should be in up up state when connected to a device.

Interface will negotiate duplex and speed on interface by default e.g. a-full (auto full) or a-100 (auto 100mb/s)

Each interface on a switch has its own collision domain
#### Configuring an interface
```cisco
# configure terminal
# interface f0/1
# speed ? - to see speed options
# duplex ? - to see duplex options
# description [description]


#interface rangef0/5 - 12 - to modify intefaces by range instead of one by one
```

#### Hub - Half Duplex Device
When 2 devices on a hub send data at the same time it will result in the hub attempting to flood both packets at the same time.

This can result in a collision when both packets are attempted to be sent through the same interface.

All devices connected to a hub are part of a collision domain.

###### CSMA-CD
Carrier Sense Multiple Access with Collision Detection

Before sending frames devices listen to the collision domain until they detect other devices are not sending.
If a collision occurs, device sends a jamming signal to inform.
Each device will wait a random period of time before sending frames.
### Auto Negotiation
Interfaces advertise their capabilities to their neighboring devices and they negotiate the best speed and duplex settings they are both capable of.

If the speed of the host is lower than the speed of the interface, the host will use its full speed while the switch will adjust the speed of its interface to match accordingly.

#### Auto-Negotiation Failures
	Speed
- The switch will try to determine the speed the connected device is running at.
- If this fails it will use the slowest supported speed/

	Duplex
- If the speed is 10 or 100 Mbps the switch will use half duplex
- If the speed is 1000 Mbps or higher, the switch will use full duplex

If duplex settings do not match, collisions will occur.

### Interface Errors
- RUNTS - Frames that are smaller than minimum ethernet frame size (64 bytes)
- GIANTS - Frames that are larger than maximum frame size (1518 bytes)
- CRC - Frames that failed the CRC check
- FRAME - Frames that have an illegal or incorrect format
- Input Errors - total of various counters
- Output Errors - Frames the switch tried to send but failed due to an error
