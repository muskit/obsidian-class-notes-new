**some terms**
- *node*: hosts/routers
- *links*: communication **channels** that connect nodes

Recall the network layers:


The link layer sits between **network** and **physical** layers
- implemented in the network interface card
- combination of sw and hw

## Error checking

Parity checking
- single-bit parity: detect single-bit errors

Checksum

Cyclic Redundancy Check (CRC)
- the most widely-used error-checking method
- vesions: CRC-8, -16, -32
Given D + R where D is data binary bits and R is some bit pattern...
- after running through a formula, ensure calculated remainder is consistent

# Links, access protocols

## Two types of links
Point-to-point - direct link between ethernet switch and host
Broadcast - shared wire (ie. ethernet, "Wi-Fi", 4G)

## Multiple-access protocols: resolving the issue of devices transmitting **simultaneously**

### Channel Partitioning
TDMA: Time Division Multiple Access
- each station is given some way to determine the **time** they can use channel
- access to channel is given in "rounds"
- unused time slots become idle

FDMA: Arequency Division Multiple Access
- channels is divided into frequency bands, assigned per station

### Random access
Slotted ALOHA - like time division, but with **randomness**
- all time frames are same size
- each station constantly attempts transmission until successful
	- fails when simultaneous connection is attempted, resulting in *collision*
	- **wait time until next attempt is random**
- conceptually simple, still not efficient way of handling collisions

CSMA (Carrier Sense Multiple Access)
- issue: we can't easily sense imminent collision due to propagation delay
	- a collision may already be imminent despite not detecting any received packets
	- solution: abort transmission upon detecting collision, send jam signal, potentially resort fallback methods

### "Taking turns" protocols
- a mix between partitioning and random access

Polling: master node invites other nodes to transmit in turn
- issue: latency, single point of failure

# MAC Address
48-bit value that uniquely identifies the network-layer device
- usually associated with a typical 32-bit IPv4 in a network
- typically set by the manufacturer, but can also be set by software

**ARP**: mapping of MAC address to IP address
  - MAC = link layer
  - IP = network layer

# Link-layer devices
### Ethernet
*3 important points*
- connectionless: no handshake between NICs
- ureliable: no ACK or NAK
- CSMA/CD for collision detection

ethernet standards
- speeds vary by physical-layer cable types:
	- 2 Mbps
	- 10 Mbps
	- 100 Mbps
	- 1 Gbps
	- 10 Gbps
	- 40 Gbps

### Ethernet switch
is an **active** device that *stores* and *forwards* network frames

### Switch vs. Router
switch ('layer 2')
- has a MAC address
- store and forward: link-layer
- forwarding: learn forwarding table using flooding/broadcasting, learning, 
router ('layer 3')
- has an IP address
- store and forward: network-layer
- forwarding: compute tables using routing algorithms


# VLAN (Virtual LAN)
*// TODO*

# Forwarding 
// TODO

# Datacenter Networking