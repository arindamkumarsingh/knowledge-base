# Internet

Hosts and end systems : All the devices which are connected to the internet.

These end systems are connected together by network of communication links and packet switches.

Whenever sender end sends data, it get divided into segments of data and add header bytes to each segment, these are known as packets.Then after it is fully recieved by end system it gets reassembled.

**Packet switch** = It takes a packet arriving from incoming communication links and forwards it to outgoing communication links.

Two most important packet switches are *routers*(network core) and *link-layer switches*(access networks).

The communication links and packet switches abd starting and ending point of the system is known as route or path.

**ISPs** = End systems access the internet through ISPs, from local to university level isps, they provide wifi in various public to private places. 

Packet switches, end systems and other parts of internet runs on protocols, mainly **TCP**(Transmission Control Protocol) and **IP**(Internet Protocol).

### Services POV

Now lets think of internet as an infrastructure, services to application(Streaming, multi-player gaming, google maps etc.)- these are called **distributed applications.**

Now when we program to make an DA, we can write a program in one end system and instruct the internet to deliver data to other end systems, but how?


