#ccna-day52 

### Access Layer
The layer that end hosts connect to, where QoS marking is typically done.
Security services like port security, DAI etc... are performed here.

### Distribution Layer
Aggregates connections from Access Layer Switches.
Typically the border between Layer 2 and Layer 3.
### Core Layer
Connects distribution layers together in large LAN networks.
Focus on speed, so CPU intensive operations should be avoided.
All connections are layer 3 and should retain connectivity throughout the LAN, even if devices fail.