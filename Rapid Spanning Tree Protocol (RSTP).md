#ccna-day22 

### Overview
- RSTP serves the same purpose as STP, blocking specific ports to prevent Layer 2 loops.
- RSTP elects a root bridge with the same rules as STP.
- RSTP elects root ports with the same rules as STP.
- RSTP elects designated ports with the same rules as STP.

The root port role remains unchanged in RSTP:
- The port that is closest to the root bridge becomes the root port for the switch.
- The root bridge is the only switch that doesn't have a root port.

The designated port role remains unchanged:
- The port on a segment (collision domain) that sends the best BPDU is that segments designated port (only one per segment).

##### Alternate Port Role
- The RSTP alternate port role is a discarding port that receives a superior BPDU from another switch.
- Functions as a backup root port.
- If the root port fails, the switch can immediately move its best alternate port to forwarding.

##### Backup Port Role
- The backup port role is a discarding port that receives a superior BPDU from another interface on the same switch.
- This only happens when two interfaces are connected to the same collision domain (via a hub)


Switches age the BPDU information much more quickly. In rapid STP a switch considers a neighbor lost if it misses 3 BPDUs. It will then flush all MAC addresses learned on that interface.

### Port States

| State      | Send / Receive BPDUs | Regular Traffic | Mac Address Learning | Stable / Transitional |
| ---------- | -------------------- | --------------- | -------------------- | --------------------- |
| Discarding | NO / YES             | NO              | NO                   | Stable                |
| Learning   | YES / YES            | NO              | YES                  | Transitional          |
| Forwarding | YES / YES            | YES             | YES                  | Stable                |

### Link Types
RSTP distinguishes between three different link types.

- **Edge** - a port that is connected to an end host. Moves directly to forwarding without negotiation.
- **P2P** - a direct connection between two switches.
- **Shared** - a connection to a hub. Must operate in half-duplex mode.
### Costs

| Speed    | RSTP Cost |
| -------- | --------- |
| 10 Mbps  | 2,000,000 |
| 100 Mbps | 200,000   |
| 1 Gbps   | 20,000    |
| 10 Gbps  | 2000      |
| 100 Gbps | 200       |
| 1 Tbps   | 20        |
