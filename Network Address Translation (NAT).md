#ccna-day44 #ccna-day45

### Overview
RFC 1918 specifies the following IP ranges as private.
**10.0.0.0/8**
**172.16.0.0/12**
**192.168.0.0/16**

NAT is used to modify the source and or destination IP of packets to allow hosts with private IP addresses to communicate with hosts over the internet.

### Static NAT
Statically configuring a one to one mapping of private IP addresses to public IP addresses.

An *inside local* IP address is mapped to an *inside global* IP address.
- **Inside Local** - The IP address of the inside host from the perspective of the local network. The private IP address
- **Inside Global** - The IP address of the inside host from the perspective of the global network. The public IP address.
- **Outside Local** - The IP address of the outside host from the perspective of the local network.
- **Outside Global** - The IP address of the outside host from the perspective of the global network.

Unless destination NAT is used the **OL** and **OG** addresses will be the same.
#### Configuration
```ios
// define the inside interfaces connected to the internal network
(config)# int g0/1
(config-if)# ip nat inside

// define the outside interfaces connected to the external network
(config)# int g0/0
(config-if)# ip nat outside

// configure the one to one IP address mappings
(config)# ip nat inside source static INSIDE-LOCAL-IP INSIDE-GLOBAL-IP

// show nat mappings
#show ip nat translations

// statistics
#show ip nat statistics
```

### Dynamic NAT
In dynamic NAT, the router dynamically maps *inside local* addresses to *inside global* addresses as needed.

An [[Access Control Lists (ACLs)|ACL]] is used to identify which traffic should be translated.
- If the Source IP is permitted by the ACL, the source IP will be translated
- If the Source IP is denied by the ACL, the source IP will not be translated

A **NAT Pool** is used to define the available *inside global* addresses.
They are still mapped one to one. 

If there is not enough *inside global* IP addresses, it is called NAT pool exhaustion.
- The router will drop the packet
- Dynamic NAT entries will time out automatically or clear them up manually.

#### Configuration

```ios
// define the inside interfaces connected to the internal network
(config)# int g0/1
(config-if)# ip nat inside

// define the outside interfaces connected to the external network
(config)# int g0/0
(config-if)# ip nat outside

// define which traffic should be translated
(config)# access-list 1 permit 192.168.0.0 0.0.0.255

// define the pool of inside global IP addresses
(config)# ip nat pool POOL1 100.0.0.0 100.0.0.255 prefix-length 24

// configure dynamic mappings
(config)# ip nat source list 1 pool POOL1
```


### PAT (NAT Overload)
**PAT** (aka **NAT Overload**) translates both the IP Address and Port Number. By using a unique port number for each communication flow, a single public IP address can be used by many different internal hosts.

The router will keep track of which *inside local* address is using which *inside global* address and port.

#### Configuration
```ios
// identical configuration of dynamic nat except
// configure PAT by mapping the ACL to the interface and enabling overload
(config)# ip nat inside source list 1 pool POOL1 overload
```