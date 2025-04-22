#ccna-day21

### Overview
When an end host connects to a switch it is in an up up state, but it cannot immediately receive data.

STP first has to spend 15 seconds listening and then 15 seconds learning before it can enable the port into a forwarding state.

When PortFast is configured on a port, the port immediately enters the forwarding state when connected to a device.

### Configuration
```
# interface [number]
# (config-if) spanning-tree portfast
```

```ios
# (config) spanning-tree portfast default
```

Connections between hosts are almost always access links. Connections between switches are almost always trunk links.

#### Configuration on a Trunk Port
In some cases you would want to enable portfast on a trunk port.
	- A port connected to a virtualization server with many vms in different vlans
	- A port connected to a router via [[Router on a Stick (ROAS)]]

```ios
# interface [number]
# (config-if) spanning-tree portfast trunk
```

### BPDU Guard
If an interface with BPDU Guard enabled receives a BPDU from another switch, the interface will be shut down to prevent a loop from forming.

```ios
# (config) spanning-tree portfast bpduguard default
```