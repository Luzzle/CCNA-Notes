#ccna-day19 

### Overview
VTP allows you to configure VLANs on a central VTP server switch and other switches (VTP clients) will sync their VLAN database with it.
Designed for large network with many VLANs.
It is rarely used and recommended you do not use it

There are 3 versions of VTP. 1, 2, 3.
- VTP v2 adds support for token ring VLANs

**Warning**: one danger of VTP is that if you connect an older switch to the network with a higher revision number and the VTP domain matches, all switches will sync their VLAN database to that switch.
### Modes
There are 3 VTP modes. **Server**, **Client** and **Transparent**

#### Server
VTP servers can:
- Add/modify/delete VLANs
- Store the vlan database in non-volatile RAM
- Will increase the revision number every time the database is changed
- Will advertise the latest version of the VLAN database on trunk interfaces and the clients will sync
- VTP servers also function as VTP clients

#### Clients
VTP clients can:
- NOT add/modify/delete VLANs
- Do not store vlans in NVRAM (in v3 they do)
- Sync with servers of the latest revision
- Advertise their VLAN database and forward advertisements to other clients over trunk ports

#### Transparent
VTP transparent mode devices:
- Do not participate in the VTP domain and do not sync.
- Maintains its own VLAN database in NVRAM
- It can modify its own database but does not advertise
- Will forward VTP advertisements that are in the same domain.



