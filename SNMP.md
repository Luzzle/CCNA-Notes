#ccna-day40

### Overview
*Simple Network Management Protocol*
SNMP is used to monitor the status and make configuration changes to devices.

**SNMP Agent**: UDP 161
**SNMP Manager** UDP 162

There are 2 main types of devices:
1) **Managed Devices**
	- These are the devices being managed using SNMP
2) **Network Management Software**
	- The devices managing the managed devices.
	- This is the SNMP 'server'

There are 3 main operations used in SNMP
- Managed devices can notify the NMS.
- The NMS can ask devices for information about their current status.
- The NMS can tell the managed devices to change aspects of their configuration.
#### Components
##### SNMP Manager
The SNMP Manager is the software on the NMS that interacts with the manage devices.
- Receives notifications, sends requests for info or sends config changes.
##### SNMP Application
Interface for the network admin to interact with.

##### SNMP Agent
The SNMP agent is the SNMP software running on the managed devices that interacts with the SNMP manager on the NMS.

##### Management Information Base (MIB)
The structure that contains the variables that are managed by SNMP.
- Each variable is identified with an Object ID (OID).

### SNMP Messages
#### Get
A request is sent from the manager to the agent to retrieve the value of an OID or multiple OIDs. The agent will send a *response*.
#### GetNext
A request sent from the manager to the agent to discover the available variables in the MIB.
#### GetBulk
A more efficient version of the **GetNext** message (introduced in SNMPv2).
#### Set
A request sent from the manager to the agent to change the value of one or more variables. The agent will send a *response* with the new values.
#### Trap
A notification sent from the agent to the manager. The manager does not send a Response message to acknowledge that it received the trap, so these messages can be considered unreliable.
#### Inform
A notification message sent that is acknowledged with a response.
#### Response
Messages sent in response to a previous message/request.

### Configuration
```ios
(config)# snmp-server community NAME {ro | rw} -> read only or read write
(config)# snmp-server host NMS-IP version VERSION COMMUNITYNAME
(config)# snmp-server enable traps TRAP TYPES
```