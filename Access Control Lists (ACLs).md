#ccna-day34 

*see [[Wildcard Masks]]*
### Overview
- ACLs function as a packet filter, permitting or discarding traffic based on source/destination IP, ports.
- ACLs are configured globally on the router ([[CISCO IOS#Global Configuration Mode|global config mode]]).
- ACLs are an ordered sequence of ACEs.
- ACLs must be applied to an interface for it to take affect. Must be applied either inbound *or* outbound.

### Standard ACLs
Matches based on Source IP address only.
Numbered ACLs are identified with a number. 1-99 and 1300-1999.

#### Configuration
```ios
(config)# access-list NUMBER {deny | permit} IP WILDCARD-MASK
(config-if)# ip access-group NUMBER {in | out}
```

Named ACLs are configured by entering Standard Named ACL configuration mode.
```ios
(config)#ip access-list standard NAME
(config-std-nacl) #NUMBER {deny | permit} IP WILDCARD-MASK
(config-if) ip access-group NAME {in | out}
```

Resequencing ACLs
```ios
(config)# ip access-list resequence acl-id starting-seq-num increment
```
### Extended ACLs
Matches based on Source/Destination IP, Source/Destination Port etc...
They can be numbered or named just like standard ACLs.
- Numbered EACLs use the following ranges 100-199, 2000-2699.
#### Configuration
```ios
(config)# access-list NUMBER {permit | deny} PROTOCOL SRC-IP DEST-IP

(config)# ip access-list extended {name | number}
(config-ext-nacl)# SEQ-NUM {permit | deny} protocol SRC-IP DEST-IP
```

Extended ACLs should be applied as close to the source as possible, to limit how far packets travel in the network.