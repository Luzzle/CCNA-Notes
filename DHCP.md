#ccna-day39

### Overview
DHCP is used to allow hosts to automatically/dynamically learn various aspects of their network config, such as IP, subnet mask, default gateway, DNS server etc...

DHCP servers "lease" IP addresses to clients. These leases are not permanent, and the client must give up the address at the end of the lease.

DHCP servers use **UDP 67**.
DHCP clients use **UDP 68**.

### DHCP Messages

| Message  | Description                                          | Broadcast or Unicast |
| -------- | ---------------------------------------------------- | -------------------- |
| Discover | Client broadcasts a message looking for DHCP servers | Broadcast            |
| Offer    | Server offers client an IP address to use            | Broadcast or Unicast |
| Request  | Client confirms they would like this IP              | Broadcast            |
| Ack      | Server confirms                                      | Broadcast or Unicast |
| Release  | Client releases IP address back to DHCP server       | Unicast              |
### DHCP Relay
A router can be configured to act as a DHCP relay agent which forwards all clients broadcast DHCP messages to the remote DHCP server as unicast messages.

### Configuration
```ios
(config)# ip dhcp excluded-address IP
(config)# ip dhcp pool POOL -> create a DHCP pool
(dhcp-config)# network IP MASK -> specify subnet of IPs assigned
(dhcp-config)# dns-server IP -> specify the DNS server that DHCP clients use
(dhcp-config)# domain-name DOMAIN -> network domain
(dhcp-config)# default-router IP -> specify default gateway
(dhcp-config)# lease DAYS HOURS MINUTES

(config-if)# ip address dhcp
```