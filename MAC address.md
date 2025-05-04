#ccna-day5 

### Definition
6 byte address of a physical device assigned upon creation of the device.
Globally unique address

The first 3 bytes are the OUI (Organizationally Unique Identifier)
The last 3 bytes are unique to the device itself.

Written as 12 hexadecimal characters

### Types
**UAA (Universally Administered Address)** - Uniquely assigned to the device by the manufacturer.
**LAA (Locally Administered Address)** - Manually assigned by an admin or protocol.

You can identify a UAA or LAA by the 7th bit.
0 - UAA
1 - LAA

In the context of [[IPv6#EUI-64|IPv6]] addresses the meaning of the U/L bit is reversed.
UL bit set to 0: The MAC address the EUI-64 interface ID was made from was an LAA.
UL bit set to 1: The MAC address the EUI-64 interface ID was made from was an UAA.