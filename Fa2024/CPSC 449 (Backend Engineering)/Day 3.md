**Topics**
Networking Basics
Remote Procedural Calls (RPC)
- an older method of network communication
Failure Modes

*scale up*: improving a single system ("bigger" machines)
*scale out*: getting more systems (more machines)
- better to scale out if handling massive amounts of traffic

redundant databases $\neq$ backup databases
- transactions are replicated and propagated throughout systems

database caches are considered a **service** in a back-end system

## A use case for message queues
usage of message queues can help with different processing rates (ie. a mainframe will be much faster than a database server)
A possible architecture:
- Mainframe -> **msg queue** -> Windows Server -> Microsoft SQL DB

# A little bit of history
In the early internet era (90s-early 2000s) decisions were still being made on standardizing how computers communicate to each other in the backend.

The big one we started with...
## Remote Procedure Call (RPC)
For an application, a function is **implemented on some other computer** to be called from somewhere else.

Example of what we wanna do: PC1 calls `credit(acct, amt)` by sending the call to PC2. PC2 runs the function internally and returns its value to PC1.

### Implementing an RPC
#### 1. Define available functions formally in some Interface Definition Language (IDL)
Example pseudo-IDL:
```idl
service {
	proc1(int arg)
	proc2(int arg0, double arg1)
	proc3()
	...
}
```
The IDL defines data types needed in these procedures.
IDL is understandable between different programming languages/platforms.

#### 2. Write code for caller and server.
CLIENT (caller) SIDE: *stub* functions
- contains networking code -- no need to be changed
SERVER (executor) SIDE: skeleton
- where **implementation** occurs (ie. DB access)

**We don't need to worry about internal network representation**
- ideally, only the RPC program will handle all of this ("marshaling") for us

### Historical Implementations
Data passed in some binary representation (developed pre-HTTP)
- Sun RPC
	- developed by Sun Microsystems
- DCE RPC
- CORBA
	- an attempt at object-oriented RPC
- Java Remote Method Invocation (RMI)
HTTP-based implementations
- XML-RPC
	- one of the first efforts at using HTTP for RPC
	- lacked solid IDL
	- instead of defining data packets, RPC requests were sent as plain-text in HTTP
	- implementation was flawed due to developer inexperience
- SOAP (Simple Object Access Protocol)
	- *extremely misleading name*
	- also XML-based, but had stricter IDL requirements
	- still very flawed
	- popular up to **early 2000s**
- REST (**NOT RPC**)
	- developed as a response against SOAP/XML-RPC
Modern implementations (in binary)
- gRPC (Google)
- Apache Thrift

### Discoverability, Location Transparency Issues
**IDL where?**
Write yourself, or retrieve published

**How to call?**
Defined by RPC implementation

**What server is running the service?**
Some registry might provide: procedure -> address/port

There's a lot of discovering specifics that need to be worked out in order to begin working with services provided by RPCs.

**REST APIs** attempt to solve these problems.
- Data types/formats
	- HTTP Content Type/Accept headers
- Uniform Interface
	- HTTP Verbs: POST GET PUT DELETE
- URLs
	- server, port, path, protocol

**GraphQL** attempts to improve on REST on these issues:
- **over-fetching:** pulling more data than we need for our context
- **under-fetching:** requiring multiple calls to build our fetched information
- GraphQL solves this by building our request and specifying what fields we want to retrieve
# Homework for next class
## Exercise 1
https://docs.google.com/document/d/1zrunmZtNfrwxqfiTL4vfdQCiocMws8NWMeqjq5vhx64

Given:
- a database with a schema for a **music store**
Task:
- setup APIs for the database
	- REST: `sandman2`
	- GraphQL: `tuql`
- create a client in Python to pull data from these APIs