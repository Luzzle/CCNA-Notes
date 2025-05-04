#ccna-day31 #ccna-day32

### Overview
Exists as a solution to the lowering number of IPv4 addresses available. 
Consists of 8 quartets of hexadecimal values.

::/0 - router has not configured its IPv6 Address
::1 - loopback address
#### Finding the IPv6 Prefix
- Typically an enterprise requesting IPv6 addresses from their ISP will receive a /48 block.
- Typically IPv6 subnets use /64
- Meaning 16 bits for subnets
- 64 bits for hosts

`2001:0DB8:8B00:0001:0000:0000:0000:0001:`
**2001:0D88:8B00** - 48 bit global routing prefix assigned by ISP
**0001** - subnet
**0000:0000:0000:0001** - hosts
#### Shortening IPv6 Addresses
- Leading 0's can be removed.
- Consecutive quartets of 0's can be replaced with a ::. **This can only be done once in an IPv6 address**
#### Expanding IPv6 Addresses
- Put leading 0s where needed.
- If a double colon is used, replace it with all-0 quartets until there are 0 total quartets.

### Configuration
```ios
# int [interface]
(config-if)# ipv6 address [address]
```

```ios
# show ipv6 interface brief
GigabitEthernet0/0 [up/up]
	FE80::EF8:22FF:FE36:8500 - link local address (automatically configured)
	2001:DB8::1 - ipv6 network address
```

### EUI-64
- EUI stands for Extended Unique Identifier
- Method of converting 48 bit [[MAC address|MAC]] into a 64 bit interface identifier
- The interface identifier can then become the 'host portion' of a /64 IPv6 address

1) Divide the MAC address in half.
2) Insert FFFE in the middle
3) Invert the 7th bit

#### Configuration
```ios
(config-if)# ipv6 address [address] eui-64
```

### Global Unicast Addresses
Global Unicast Addresses are public addresses which can be used over the internet.
Must register to use them. Must be globally unique.

Originally defined as the 2000::/3 block (2000:: to 3FFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF).
Now defined as all addresses which aren't reserved for other purposes.

### Unique Local Addresses
Unique local IPv6 addresses are *private addresses* which cannot be used over the internet.
`FD45:93AC:8A8F:0001:0000:0000:0000:0001/64`

**FD**: Indicates a unique local address
**45:93AC:8A8F**: 40-bit 'global ID' which should be randomly generated.
**0001**: 16 bit subnet identifier.

### Link Local Addresses
Automatically generated on IPv6 enabled interfaces.
Uses the address block FE80::/10.

All link local addresses begin with FE8.

### Multicast
IPv6 uses range FF00::/8 for multicast. (FF00:: to FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF)

| Purpose           | IPv6 Address |
| ----------------- | ------------ |
| All nodes         | FF02::1      |
| All routers       | FF02::2      |
| All OSPF routers  | FF02::5      |
| All OSPF DRs/BDRs | FF02::6      |
| All RIP routers   | FF02::9      |
| All EIGRP routers | FF02::A      |

Multicast scopes
- **Interface-local** (FF01)
	- The packet doesn't leave the local device. Can be used to send traffic to a service within local device.
- **Link-local** (FF02)
	- The packet remains in the local subnet.
- **Site-local** (FF05)
	- The packet can be forwarded by routers. Usually kept within a single physical location.
- **Organization Local** (FF08)
	- Wider in scope than site-local
- **Global** (FF0E)
	- No boundaries

### Anycast
Multiple routers are configured with the same IPv6 address.
They use a routing protocol to advertise the address.
When hosts send packets, routers will forward it to the nearest router configured with that IP address.

Configured using a regular unicast address and specify it as a multicast address.