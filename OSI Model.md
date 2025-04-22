#ccna-day3

*see [[TCP-IP Suite]]*

**O**pen **S**ystems **I**nterconnection Model
## Definition
OSI is a [[Networking Model|networking model]] to create [[Protocol Data Units]]

## Layer 7 - Application
End user layer that interacts with software applications with a communication unit.

*Functionalities*
- Identifying communication partners
- Synchronizing communication

*Example protocols*
- HTTP/HTTPS

## Layer 6 - Presentation
Data is translated between application and network formats.

*Functionalities*
- E.g. encryption of data as it it sent
- Also translates between different Application-layer formats

*Example protocols*
- ASCII
- JPEG
- PNG
- MP3

## Layer 5 - Session
Controls sessions between communicating hosts

*Functionalities*
- Establishes, manages, and terminates connections between local application and the remote application.

*Example protocols*
- SMB
- RPC
- RTCP
- SCP
- PPTP

## Layer 4 - Transport
Segments and reassembles data for communications between end hosts.

*Functionalities*
- Breaks large pieces of data into smaller segments which can be more easily sent over the network.
- Provides host to host communication

*Example protocols*
- TCP
- UDP
- DCCP
- SCTP

## Layer 3 - Network
Provides connectivity between end hosts on different networks

*Functionalities*
- Provides logical addressing
- Provides path selection between source and destination

*Example protocols*
- RIP
- OSPF
- BGP
- IP

## Layer 2 - Data Link
Provides node to node connectivity and data transfer (e.g. PC to switch, switch to router)

*Functionalities*
- Defines how data is formatted for transmission over a physical medium
- Detects and corrects physical layer errors
- Switches operate at Layer 2

*Example protocols*
- [[Ethernet|Ethernet]]
- PPP (Point to Point Protocol)

## Layer 1 - Physical
Defines physical characteristics of the medium used to transfer data between devices.

*Functionalities*
- E.g. voltage levels, max transmission distances, cables specs.
- Digital bits are converted into electrical or radio signals
