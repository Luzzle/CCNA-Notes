#ccna-day16

[[Router on a Stick (ROAS)]]

[[Dynamic Trunking Protocol (DTP)]]
[[VLAN Trunking Protocol (VTP)]]

A LAN contains all devices within the same broadcast domain.

![[Pasted image 20250409062055.png]]
Although there are 3 subnets, they are all on the same broadcast domain.

### Overview
VLANs are configured on switches on a per-interface basis
They logically separate end hosts at Layer 2

Switches do not forward traffic directly between hosts in different VLANs.
- VLANs 1, 1002-1005 cannot be deleted and exist by default

**Access Port**: An access port is a port that belongs to a single VLAN and usually connects to an end host like a PC

**[[Trunk Ports]]**: A switchport that carries multiple VLANs.

```ios
# interface [range or interface number]
# switchport mode access
# switchport access vlan [number]
```

```ios
# vlan 10
# name [NAME]
```


### VLAN Tagging
There are 2 main trunking protocols ISL (Inter-Switch Link) and IEEE 802.1Q
ISL is an old Cisco proprietary protocol.

##### 802.1Q
802.1Q inserts a 4 byte field between Source and Type/Length field of the Ethernet header.
2 main fields:
- TPID: Tag Protocol Identifier
	- Always set to a value of 0x8100.
- TCI: Tag Control Information
	- PCP (Priority Code Point)
		- 3 bits in length
		- Used for Class of Service (COS) to prioritize service
	- DEI (Drop Eligible Indicator)
		- 1 bit
		- Indicates if frame should be dropped in network congestion
	- VID (VLAN ID)
		- 12 bits
		- Identifies which VLAN the frame belongs to
		- 4096 total VLANs

VLANS 0 and 4095 are reserved and cannot be used
Actual range is 1-4094

**Native VLAN**
The native VLAN is VLAN 1 on all trunk ports by default, however this can be manually configured on each trunk port.
The switch does not add a tag to native VLANs.
When a switch receives an untagged port it assumes it is part of the native VLAN.

*Setting native VLAN*
```ios
# int g0/0.10
# encapsulation dot1q [vlan-id] native
```

### VLAN Ranges
VLANs are divided into 2 ranges
- Normal VLANs: 1-1005
- Extended VLANs: 1006 - 4094


