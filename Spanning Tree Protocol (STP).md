#ccna-day20 #ccna-day21


[[STP Versions|Versions]]

**Broadcast Storm**: If a network has too many broadcast frames looping between connected switches, they can loop infinitely and cause a broadcast storm.
### Overview
- Switches from all vendors run STP by default.
- STP prevents Layer 2 loops by placing redundant ports in a blocking state.
- Interfaces in a forwarding state behave normally.
- Interfaces in a blocking state can only send or receive STP messages called BPDUs (Bridge Protocol Units)

Interfaces can be placed in a blocking state which prevents loops from occurring in a network whilst still allowing for redundancy.

If a forwarding interface goes down, the switches will automatically enable a blocked interface to adjust the topology and ensure connectivity and uptime.

[[PortFast]]

### How it works
By selecting which ports are forwarding and which are blocking STP creates a single path to and from each point in the network.

##### Finding the root switch
STP-enabled switches will send a Hello [[BPDU]] out of all interfaces once every 2 seconds.
If a switch receives a Hello BPDU it knows it is connected to a switch on that interface.
- When a switch is powered on it assumes it is the root bridge, only giving up that position if it receives a superior BPDU.
Once the topology converges and all switches agree on a root bridge, only the root bridge will send BPDUs.

##### Finding the root port
Each remaining switch will select 1 of its interfaces to be its root port, the interface with the lowest root cost will be the root port.

| Speed    | Cost |
| -------- | ---- |
| 10 Mbps  | 1000 |
| 100 Mbps | 19   |
| 1 Gbps   | 4    |
| 10 Gbps  | 2    |
###### Tiebreakers
**Lowest neighbor bridge ID**
**Lowest neighbor port ID**
- port priority + port number

##### What ports to block
Each remaining collision domain will select ONE interface to be a designated port. The other port in the collision domain will be non-designed and blocked.
1) Interface on the switch with the lowest root cost
2) Interface on the switch with the lowest bridge ID

### Port States

| State      | Stable or Transitional |
| ---------- | ---------------------- |
| Blocking   | Stable                 |
| Listening  | Transitional           |
| Learning   | Transitional           |
| Forwarding | Stable                 |

**Blocking**:
- Non designated ports are in a blocking state
- Effectively disabled to prevent loops
- Do not send/receive regular traffic
- Receive BPDUs
- Do not forward BPDUs
- Do not learn MAC addresses

**Listening**:
- The listening state is 15 seconds long by default, determined by the forward delay timer
- Only forwards BPDUs
- Does not learn MAC Addresses from regular traffic on the interface.

**Learning**:
- Learning state is 15 seconds long by default
- 15 seconds long determined by the same timer
- Only sends/receives BPDUs
- Learns MAC addresses from regular traffic that arrives on the interface

**Forwarding**:
- Normal port functionality

### STP Timers
**Hello**:
- How often the root bridge sends hello BPDUs
- 2 seconds

**Forward delay**:
- How long the switch should stay in the listening/learning state
- 15 sec

**Max Age**:
- How long an interface will wait after ceasing to receive Hello BPDUs to change the STP topology.
- 20s (10 * Hello)