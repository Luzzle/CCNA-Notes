#ccna-day7

IPv4 Addresses are 32 bits in length.

### Classes

| Class | First Octet | First octet numeric range | Prefix Length | Additional Notes    |
| ----- | ----------- | ------------------------- | ------------- | ------------------- |
| A     | 0xxxxxxx    | 0-126                     | /8            |                     |
| B     | 10xxxxxx    | 128-191                   | /16           |                     |
| C     | 110xxxxx    | 192-223                   | /24           |                     |
| D     | 1110xxxx    | 224-239                   |               | Multicast Addresses |
| E     | 1111xxxx    | 240-255                   |               | Experimental Uses   |

### Loopback address
127.0.0.0 - 127.255.255.255
Used to test network stack on the local device. All traffic is sent back up the network stack as if it were sent by another device.

[[IPv4 Header]]
