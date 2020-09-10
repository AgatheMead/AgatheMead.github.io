---
layout: post
title: Packet Switching
---

## A bit of the history
Media articles usually compare the Internet to the highway system because they both have rules to follow. For highway system, the streets and paths in local communities are usually unoccupied, while most of the traffic congestion occurs on major arteries. In the old days people were connected to the internet from institutions and congestions occurred at exchange points or on the unreliable trunks (when trunks went down). 
Nowadays users connect to a shared access network with limited bandwidth. Users consume more incoming than outgoing bandwidth. Sometimes we are unaware of internet protocol, however it is very crucial because it keeps the entire network running so that information can travel across networks and arrive at the right destination.

### Transmission Control Protocol (TCP) and Internet Protocol (IP)

>> _http(s)_ is a kind of protocol. When you try to visit a webpage by clicking on its URL, the Internet Service Provider (ISP) looks up the domain name, locates the matching IP address, and sends it back. The web browser then sends a request to that returned IP address for what you are looking for.

![A example of visiting http://www.bbc.co.uk/nature/life/frog from BBC Bitesize^{1}](https://bam.files.bbci.co.uk/bam/live/content/zwb7pv4/large)

TCP/IP, also referred as the internet protocol suite, is the set of traffic rules applied to the whole internet that can transport IP packets. TCP/IP protocol was designed in 1970s by two scientists worked for DARPA - Vint Cerf and Bob Kahn, hornored as *the fathers of the Internet*^{7}. Kahn firstly set four goals for Transmission Control Protocol (TCP):
- Network connectivity. Any network could connect to another network via a router (initially they used the word 'gateway' instead).
- Distribution. No central network administration or control.
- Error recovery. Missing packets can be requested to resent. 
- Black box. No physical internal changes will be made to the network connection.
In 1973, Vinton Cerf jointed Kahn and then they created the standard protocol used on the Internet today. 
When first introduced, Internet Protocol (IP) was a wireless datagram worked concurrently with TCP. IP is in charge of addressing hosts, putting data into datagrams, and routing datagrams from source to destination across one or more IP networks. TCP is responsible for keeping track of data segmentation and forwards them to the Internet Layer (we'll get into that soon). 
The internet layering model can be breaked up into four distinct layers. The first layer is called *Application layer* that is the interface for internet users. In this level, users interact with running programs like web browsers and user requests are first initiated. 
The *Transport layer* is where the data being segmented into packets. This layer handles communication between devices on networks and the method for connection.
The segmented data from transport layer is sent along to the *Internet Layer*. This is the layer on which the Internet Protocol itself functions and takes us from point-to-point connections to graph-like networks. Data packets with affixed IP address are routed to the corresponding destinations.
The data arrives on the *Local Access Layer*, is converted into a transmittable format like binary signals. This layer handles the acutal physical transfer of the data inside the network itself.  
IP treats each packet independently, this means each packet must contain complet addressing information.

![Internet layering model, from lowest to highest, are the Local Access Layer, the Internet Layer, the Transport Layer, and the Application Layer, from CCNA Blog](https://s8182.pcdn.co/wp-content/uploads/2014/06/063014_1912_TCPIPANDTHE2.jpg)

### Packet Switch Network
The point of switching is to dynamically share a network in order to join any two nodes for communication.  Regarding sharing a network, it comes about two forms:
- Sharing a channel as generally seemed in wireless network, i.e., allowing multiple nodes to access the same communication medium at once. 
- Sharing a particular link within a network for switches, i.e., multiplexing packets from multiple edges onto a single outgoing link.

![Conclusion of existing switching techniques^{3}](https://www.researchgate.net/profile/Hossam_Hassan4/publication/261795895/figure/fig8/AS:357928210059274@1462348143789/Switching-techniques.png)

Sending small packets allows a more than one message share a node at the same time. Packet switching also helps to avoid jamming the network while transmitting message. If the recipient finds some packets are missing, it can request the source just resent those missing packets rather than resent the whole message.  

![The full circle of Packet Switching](https://4.bp.blogspot.com/-Qb-TM6Eq28w/VVQfK7Zd2KI/AAAAAAAAAB8/I9ff8x4aIS0/s1600/PacketSwitched.gif)

- Data is firstly divided into small payloads from the transport layer, and the payloads which have headers indicating their destination are refered as *packets*. 
- Packets in queue are then transmitted individually across the network.   
- And finally the message is reassembled into the correct order in the destination. 

Pros             | Cons
---------------- | -----------
No set-up time   | Lost packets when congestions occur
No wasted resources | Packets in queue may be re-ordered by network
Good match to bursty traffic | Computes path decision in each router
Robust behavior for downlink or router | Each packet carries more information
Good adaption of routing algorithms | Buffers at routers as packets are in queue

Packet switching is the better method for many cases, especially for large media files. The problems left to solve are the following:
1. How to determine routes to destinations? (routing algorithms)
2. How to discover a routing failure? (another story)

## Dijkstra's Algorithm and Short-Path Routing
IP makes no guarrentee each packet reach its destination, nor it take any corrective action if a packet fails to reach the destination. Packet switch network topology can be represented by a minimum weight spanning tree of a weighted graph. There are two classes of shortest path algorithms:
- Distance vector (Bellman-Ford Algorithm). Requires local cost estimates, can suffer from slow convergence and routing loops.
- Link state (Dijkstra's Algorithm). Requireds global cost estimates, but are more robust and shows faster convergence. The graph must come with non-negative weighted edges.
Dijkstra's algorithms find the shortest paths from sources to all other destinations in order. The root of the spanning tree is the source node. Each link in a network comes with an cost. These cost simply indicates how expensive it is to send a packet along that link. The cost can include factors such as deley, throughput, error rate, monetary cost, etc. With each iteration, a new node is added to the tree such that the total link cost is the lowest among any other node not in the tree. 

Effetive routing requires all switch to perform a shortest path on a network graph. Short-Path algorithms have polynomial complexity^{8}. Each node can individually route packets to a particular destination by calculating the shortest path from itself to the destination node.

![Path Planning](https://miro.medium.com/max/700/1*ImqF9ZyNVws63HK-ZuxlGQ.png)

### Application of Dijkstra's Algorithm
In practical world, we can find many applications of Dijkstra's algorithm. 
- Mapping. An example would be Deliveroo divers require a software that finds the shortest path between current location and the delivery destination to avoid the extra delay. 
- Social Networking Application. We often get a list of friends suggestions in social media Apps. Dijkstra's algorithm can be applied using shorest path between users measured in connections.
- Travel Agenda. Imagine that a travel agent is making an agenda of flights for his clients. Given the departure city and destination, departure time and arrival time, the solution can easily sorted by Dijkstra-based methods. 

### Complexity of Dijkstra's Algorithm
Let *N* being the number of nodes *{V}* in the network, and *L* denotes the number of links in the network. The complexity is determined by the search operation in each setp to pick out the node with minimum cost so far *u* from *V*. Each link counts towards two neighbors, thus there are in total *2L* neighbouts to be inspected. If we use linear search, then the complexity will be *O(N^2+L)*. If the node set are store in a heap data structure, the complexity will be *O(NlogN +L)*.

## TBC
We stopped supporting circuit switching and passed to packet switching completely after upgrading from 3G to 4G/LTE. LTE networks deliver all user traffic in IP packets, and provide always-on IP connectivity between UE and network. When a user (i.e. UE) initially attaches to the packet data network, an address is assigned to the user. 
There will be more and more heterogeneous devices relying on cellular networks for data exchanges. 5G architects shows fantastic performance on reducing latency with higher bandwidth requirements. This means that the IP will also need to be upgraded. 

## Externel links
[1] https://www.bbc.co.uk/bitesize/guides/zp9jpv4/revision/

[2] http://user.it.uu.se/~carle/Notes/20_Switching_and_Multiplexing.html

[3] Hassan, Hossam. (2014) Hardware Implementation and Evaluation of Flexible Router Architecture for NoCs. 10.13140/RG.2.2.25573.55527.

[4] https://www.coursera.org/lecture/friends-money-bytes/packet-switching-uWqch

[5] https://www.coursera.org/lecture/packet-switching-networks-algorithms/dijkstra-algorithm-2676k

[6] https://www.coursera.org/learn/tcpip 

[7] https://history-computer.com/Internet/Maturing/TCPIP.html 

[8] http://www.cs.toronto.edu/~marbach/COURSES/CSC358_S18_1/shortest_path.pdf

----
****
