---
Title: Module  6 - C&C Views
Author: Neil Ernst
marp: true
---
 
# Representing Views

The style we chose (layers, uses, etc) are often thought of as **primary presentations**. A primary presentation is the graphical representation of the view, but does not in itself constitute documentation. What are some of the problems with doing it that way?

----
They include 
- not disambiguating various elements of the diagram; 
- missing rationale; 
- missing data points that help answer e.g. latency questions, 
- capturing strange cases like shutdown behavior, 
- and other items that would clutter or confuse the diagram. 

There is a strong argument to be made that this information *should* be on the diagram itself. In many situations, all you get is a 10 slide Powerpoint deck with a bunch of diagrams. It sure would help to have more details. 


----
# Component and Connector Views (p. 332)
*Elements*: **components**: principal units of runtime interaction and data stores and connectors: interaction mechanisms
*Relations*: **attachment** of components’ ports to connectors’ roles (interfaces with protocols)
*Properties*: name, relevant QA

----
## Why We Care - questions C&C views can answer
* Specifying the behaviour that elements must exhibit
* Show how the system "works"
* Reasoning about runtime system quality attributes such as performance, security, and reliability
* What are the major executing components?
* Which parts of the system are replicated?
* Data Flows
* Which parts of the system can run in parallel?

----
# Instances of C&C Views - Styles
1. Pipe and Filter
2. Client-Server
3. Shared Data
4. Pub-Sub
5. Service Oriented

----
# Pipe and Filter
Show dataflow. Filters transform data and pass it along Pipes. Analyze system throughput, function composition.

*Elements*: Filters, data transducers as components. Pipes as one way data conduits.
*Relations*: ports connecting pipes and filters.
*Constraints*: restrict loops and branches.

![P&F example from Unix](img/unixpipe.png)

----
# Client-Server
Shows modifiability and reuse possible in a 2 tier architecture. Analyze availability, connections expected, requests, interface needs.

*Elements*: Client invokes services from Server. Request/reply connector joins them.
*Relations*: attach client to server
*Constraints*: number of tiers; how connections are made;

![Web scalability image](http://aosabook.org/images/distsys/imageHosting3.png)

----
# Exercise
With a partner, sketch a client-server diagram for a multiplayer game like [DOTA](http://www.dota2.com/play/) or Fortnite.

----
# Shared Data
Read and write to a shared data store. Analyze data needs, identify who connects.

*Elements*: data stores and accessors.
*Relations*: attachments.
*Constraints*: how the data is attached via connectors.

![Package data](http://aosabook.org/images/packaging/pypi-workflow.png)

----
# Pub-Sub
Decouple **listeners** from **publishers**. A very common pattern (e.g. Observer, which we look at later), it essentially wraps up asynchronous/callback architectures. Helps isolate consumers and producers, analyze decoupling and independence in your architecture.

*Elements*: publisher and subscribers. Possibly the bus for distributing messages
*Relations*: attachments.
*Constraints*: who can listen, message semantics.

----
![Bitbake, showing a combined view](http://aosabook.org/images/yocto/aosa3.jpg)

----
# Services and Microservices
Allows for easy interoperability based on common messaging layer. Use robust and proven architectural patterns (REST). [Microservices (e.g. at Netflix)](https://www.infoq.com/presentations/netflix-chaos-microservices/) are small, independent service providers that belong to a single organization.
* *Elements*: service providers, service consumers, middleware
* *Relations*: typically HTTP messages using the HTTP verbs (GET/POST/DELETE etc) but also SOAP/XML and others
* *Constraints and challenges*: who can consume messages, authentication requirements, observability approach, duplication of functionality

----
![](https://www.honeycomb.io/wp-content/uploads/2018/10/netflix-microservices-traffic-flow-768x466.png)