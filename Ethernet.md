#ccna-day5

### Ethernet Header
The preamble and SFD are not usually considered as part of the ethernet header

- Preamble
	- 7 bytes
	- Allows devices to synchronize their receiver clocks
- SFD: Start Frame Delimiter
	- 1 byte
	- Marks the end of the preamble
- Destination:
	- 6 Bytes
	- L2 address of the device receiving the frame
	- Unicast frame: frame destined for a single target
	- [[MAC address]]
- Source: L2 Address
	- 6 Bytes
	- L2 address of the device sending the frame.
- Type: L3 Protocol (can be a length field)
	- 2 Byte
	- A value of 1500 or less the field indicates the length of the encapsulated packet in bytes.
	- A value of 1536 or greater in this field indicates the type.
	- 0x0800 = IPv4, 0x86DD IPv6
### Ethernet Trailer
- FCS: Frame Check Sequence
	- 4 Bytes
	- Detects corrupted data by running a CRC check on the data

