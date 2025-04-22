#ccna-day20 

### Overview
Switches use the Bridge ID field to elect a root bridge for the network.
The switch with the lowest Bridge ID become the root bridge.

On the root bridge all ports are forwarding.

\[Bridge Priority]\[Mac Address]

The bridge priority is compared first and is 32768 by default. The lowest mac address is then used as a tie breaker.
