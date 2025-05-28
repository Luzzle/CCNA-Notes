#ccna-day55

### Overview
The standards we use for wireless LANs are defined in IEEE [[802.11 Frame|802.11]]

#### Wireless Concerns
1) All devices within range receive all frames.
2) Wireless communications are regulated
3) Wireless signal range must be considered.

[[Distribution Systems]]
### Channels
The 2.4Ghz band is divided into several channels, each with a 22mhz range.

For adjacent Access Points (AC) it is recommended channels **1, 6 and 11** to ensure there is no interference.
![[Pasted image 20250526141815.png]]

### Service Sets
802.11 defines different *service sets* which are groups of wireless network devices.
There are 3 main types:
- Independent
- Infrastructure
- Mesh

All devices in a service set share an SSID (Service Set Identifier) which is a human readable name and does not have to be unique.

#### IBSS (Independent Basic Service Set)
An **IBSS** is a wireless network in which two or more wireless devices connect directly without using an AP.

Also called an ad hoc network. Can be used for file transfer like AirDrop.

#### BSS (Basic Service Set)
A BSS is a type of Infrastructure Service Set where clients connect to each other via an AP but not directly with each other.

The **BSSID** is used to uniquely identify the AP.
- Other APs can use the same SSID but not the same **BSSID**.
- The BSSID is the MAC address of the AP radio.

Wireless devices request to [[802.11 Frame#Association Process|associate]] with the BSS and are called clients.
The area where a BSS is usable is called the **Basic Service Area**.

#### ESS (Extended Service Set)
To create large wireless LANs beyond the range of a single AP.

Each AP with their own BSS are connected by wired network.
- Each shares an SSID but has a unique BSSID and use a different channel to avoid interference.

**Roaming**: Clients can pass between APs without having to reconnect.

The BSAs should overlap about 10-15%

#### MBSS (Mesh Basic Service Set)
An **MBSS** can be used in situations where its hard to run ethernet between APs.

At least one AP is connected to the wired network. The **RAP (Root AP)**, the rest are called **MAP (Mesh AP)**.
A protocol is used to determine the best path through the mesh.


### AP Deployment Methods
#### Autonomous AP
Self contained systems that don't rely on an [[Wireless LAN Controller|WLC]].

These can be configured individually.
- A remote IP for management should be configured.
- RF (Radio Frequency) params must be configured
- Security policies are handled individually by each AP.

All are connected via trunk link and VNETs are stretched across the entire network.
#### Lightweight AP
The functions of the AP are split between itself and the [[Wireless LAN Controller|WLC]].

LAPs handle real-time operations whilst WLC will handle deeper configuration operations.
This is called a **split-MAC architecture**.

The location of the WLC can be flexible and it authenticates with the LAP through digital certificate (X.509 certs).

Lightweight APs can be configured in various modes
- **Local** - default mode where they offer a BSS for clients to associate with
- **FlexConnect** - Allows traffic to be switches between wired and WLC if the WLC goes down.
- **Sniffer** - The AP does not advertise and simply captures traffic
- **Monitor** - Does not advertise and receives frames to detect rogue traffic
- **Rogue Detector** - Only listens to wired traffic receives a list of suspected rogue clients. Listens to ARP on the wired network and correlates with WLC traffic.
- **Flex plus bridge** - Adds FlexConnect functionality to mesh networks.
##### CAPWAP
WLCs and LAPs use a protocol called **CAPWAP** **Control and Provisioning of Wireless Access Points** which is based on an older protocol called **LWAPP (Lightweight Access Point Protocol)**

Two tunnels are created.
- Control Tunnel (UDP 5246) - used to configure the APs and is encrypted by default.
- Data Tunnel (UDP 5247) - traffic is sent through this tunnel to the WLC (does not go directly to the wired network). Can be encrypted with DTLS (Datagram TLS)
	- Note from Cristian: TLS is primarily for TCP, DTLS is for UDP

WLCs connect to Access ports not trunk links.
##### Benefits
- Scalability
- Dynamic channel assignment
- Transmit power optimization
- Self healing wireless coverage
- Seamless roaming
- Client Load Balancing
- Security / QoS management

#### Cloud-based AP
Autonomous APs that are centrally managed on the cloud like Cisco Meraki.