#ccna-day29

### Overview
A first hop redundancy protocol is a computer networking protocol which is designed to protect the default gateway used on a subnetwork, by allowing 2 or more routers to provide backup for that address.

In the event of a failure of an active router, the backup router will take over the address, usually within a few seconds.

### Configuration
A virtual IP is configured on the 2 routers and a virtual MAC is generated for the virtual IP. (Each FHRP uses a different format for the virtual MAC).

An active router and a standby router is elected.
End hosts in the network are configured to use the virtual IP as their default gateway.

The active router replies to ARP requests using the virtual MAC address, so traffic destined for other networks will be sent to it.

If the active router fails, the standby becomes the next active, by sending gratuitous ARP messages so that the switches update their MAC address tables.

You can configure 'preemption' so that the old active router does take back its old role.

### Protocols
[[Hot Standby Router Protocol (HSRP)]]
