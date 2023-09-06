We will be using Python 3.11
- "batteries-included" programming language

<u>Framework types</u>
Model-View-Controller (MVC)
- Django
Micro-framework - handles simpler tasks
- FAST API, Flask
- ex: map a request's path directly to a Python function

# Architecture of a back-end Server
client <--> server
- communications occur in HTTP(S)
- client makes **requests**
	- ie. web browser; user agent
- server creates **responses** to requests
	- may contact other **database** systems to formulate the response

The "three-tier" system:
- client
- server
- databases
Old concept; still mostly applies today
- servers typically also respond with data (JSON, XML, etc.) in addition to frontend-rendered content (HTML, CSS, JS)

To the front-end, the back-end is **abstracted**
- numerous systems working together in a maze-like flow is effectively invisible to front-end developers, where they can just make API calls and work with responses

<u>back-end types</u>
Monolithic: all API calls (GET /a/b/c, PUT /d/e/f, etc.) are handled by **one** application
- one program, running on one machine
Microservice: each function/API call belongs to a particular service (their own program)
- lets each service be deployed on separate hosts
- each service might have their own DB
- ***flexibility***
"Server-less": abstracts the API-call to code pipeline
- everything in the middle is handled by some service provider
- "functions as a service"
- developer has less control over deployment: a pro *and* a con

## Load Balanced System
A **load balancer** handles massive incoming traffic among multiple servers
- decides which server handles a received request
- mitigate server failure
- easily scales up # of servers
- many servers typically share one single database system
	- DBs are made to handle massive traffic alone
	- sometimes a **replica** database is available in case the main database goes offline
- typically deployed on **frontend** and **CDN** servers, but can be deployed on the **back-end** as well
	- LB --> 3 FRONTENDs ==> **LB** --> 3 BACK-ENDs ==> 1 REPLICATED DB
- depending on application, multiple database systems for different data might be used in a back-end system

**Distributed cache**
- allows server to quickly fetch data w/o going through database
- slowness may be due to data being **replicated (backups)** and **sharded**
- LB --> 3 FRONTENDs ==> LB --> 3 BACK-ENDs ==> **CACHE** ==> REPLICATED DBs

Most components in a large-scaled back-end server are distributed among multiple systems

Polyglot persistence
- "polyglot"- multiple languages
- storing data in multiple formats on a single DB system

### Handling heavier back-end tasks
The back-end server might other perform heavier, **time-consuming** tasks
- emails
- analytics
- image processing
- ML (facial recog., recommends, etc.)
To handle this, we could use a work **queue system**
- LB --> 3 FRONTENDs ==> LB --> **queue**, 3 BACK-ENDs ==> CACHE ==> REPLICATED DBs
- a whole other system handles this queue, w/ other **worker agents** finishing tasks in the queue

## A bigger picture
Entirety of described system above is likely housed in a **data center**
- a large company will likely duplicate data centers as redundancy backups
- a new issue: timely data dispersion