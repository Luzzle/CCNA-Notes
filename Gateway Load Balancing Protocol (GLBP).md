#ccna-day29 

### Overview
Load balances among multiple routers within a **single subnet**

An AVG (Active Virtual Gateway) is elected.
Up to 4 AVF (Active Virtual Forwarders) are assigned by the AVG.
Each AVF acts as the default gateway for a portion of the hosts in the subnet.

Multicast IPv4 Address:
- 224.0.0.102

Virtual MAC Address:
- 0007.b400.XXYY (XX - GLBP Group, YY - AVF Number)
