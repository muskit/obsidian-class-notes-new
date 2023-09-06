## Overview
__Standard Functions__
- forwarding: move packets from input link to router output link
	- analogy: going through an interchange
- routing: determine route taken by packets from src to dest. by *algorithms*
	- analogy: planning the entire trip from source to destination
- data plane: determine how datagram arriving on router input is forwarded to output
	- scope: router
- control plane: determine how datagram is routed among routers, src -> dest
	- scope: whole network
	- routers communicate to each other on the control plane by algorithms

## Router (ISP-level)
```
                            [Routing Processor]
	               Control Plane
                -----------------------------------------
                                              Data Plane
                                 |      ^
                                 |      |
                                 v      |
[Input Port] ------> [High-speed Switching Fabric] ------> [Output Port]
```
### Input Port
- interprets packet header
- **match** with forwarding table to send to device
- has queue; suffers delays and buffer overflow (drops)

Switching fabric consists of various **switches**, tracking various interface ports

Speed consistency matters; if something's too slow, we end up with delays and **dropped packets**
- datagrams arrive in queue faster than available buffer space

### Output Port
Intentionally giving packets lower priority at the ISP-level **based on source/service** is something Net Neutrality aims to destroy

Buffer Management
- we **drop** a packet when buffer is full. there are a couple approaches
	- depending on customer, we may **prioritize** certain services **given their needs** (ie. business applications)
	- **tail drop**: drop the last arriving packet
- we **mark** packets to signal congestion

Packet Scheduling Policies (how do we determine what to drop?)
- First Come First Serve (FCFS)
- Priority- discriminate by header info
	- FCFS within priority class
- Round Robin
- Weighted Fair Queueing (WFQ)

## IP Addressing
Public vs. private addresses
- private addresses are reserved for LAN devices
	- A: `10.0.0.0/8`
	- B: `172.16.0.0/12`
	- C: `192.168.0.0/16`

## Subnetting
Divide a network on the same router into *sub networks*
- isolated networks help improve security and performance
	- security: we may not want some devices to access each other
	- performance: when sending a **broadcast** datagram, there may be significantly less devices for the router to send the packet to

`/xxx` Subnet Mask Format
- determines **how many bits from the left** are NOT changable

## DHCP
**D**ynamic **H**ost **C**onfiguration **P**rotocol
- host is *dynamically* assigned an IP address upon joining a network
- allows for address reuse
- convenient for mobile users constantly joining/leaving networks

process overview
  a. host broadcasts a **DHCP discover**, checking for the existence of a *DHCP server*
	  - 255.255.255.255 broadcast
  b. server responds to host with an IP address "offer"
  c. host responds with a decided address
    - can either be desired (ie. previous address) or the server-provided
  d. server responds by confirming the decided IP address

  note: a. and b. may be skipped if host wants to use an old address

## IP Datagram
*IPv4*
![[Pasted image 20230322145315.png]]

*IPv6 (just the header; what follows is payload data)*
![[Pasted image 20230322145655.png]]
**New to IPv6**
- Priority- important for congestion control
	- assigned based on protocol
- Flow Label- distinguishes data flow
- Next Header- indicates type of "extension header"
- Hop limit- prevents infinite loop
**Removed in IPv6**
- header checksum
- fragment offset
- options
**Challenging Transition**
practically *all* devices still use IPv4; can't transition everything to IPv6 quickly
- many legacy routers still only use IPv4
to solve this, we use **tunnelling**
![[Pasted image 20230403175609.png]]
- encapsulate the IPv6 datagram as an IPv4 packet's data
- used extensively in 4G-5G comms
- implemention (pictured above) can vary between ISPs

## Generalized Forwarding
routers have a *forwarding table*, which determines what to do (forward, drop, etc.) with a received packet depending on header (ie. destination ip)

### Flow table abstraction
**OpenFlow**- protocol that allows a server to tell network switches where to send packets (match + action)
![[Pasted image 20230403180339.png]]
We can configure the server to take action based on any of the fields pictured above.
Actions: `drop`, `forward`, `modify`, `send` to OpenFlow controller

## Middleboxes
some intermediary box performing functions apart from standard functions of an IP router. sits between a source and destination host.
- ex: NAT, firewalls, load balancers (these exist on Network or Application layers), caches, app-specific boxes
- can be on dedicated hardware or software (nowadays it's typically a software)
