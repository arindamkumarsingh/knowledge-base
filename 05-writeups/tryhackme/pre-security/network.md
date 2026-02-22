# INtro

First, documented intro to internet was ARPANET in late 1960s, funded by US Defence. Later on in 1989, tim berners-lee invented WWW which internet was used as a big repo to store and share info.

Devices can be identified through mainly two things:-

* Name
* Fingerprint

Now, we can change our name of device but not the fingerprint ie, IP address and MAC address.

**IP address** is a way of identifying a host in a network for a period of time, then can communicate with other devices using the same address.

IP address has various protocols which has a common way of functioning over the internet, now it is divided into 4 octets and their values summarise the address.This is done through a method called subnetting.

A pubic network is the one found in the internet and the private network is found among other devices.

As more and more devices were connected, there was a kind of shortages in ip addresses as **ipv4** has (2^32) address approx 4.29 billion. For this shortage issues, **ipv6** was introduced which boasts 2^128 addresses Approx 340 trillion so issue solved.

### MAC ADDRESS

This is found under the chip of motherboard and act as a physical network provider. It is a 12 char hexadecimal number, divided into 6 parts, first three belongs to the vendor who built the interface and next 3 is unique.

However this addresses can easily be faked called spoofing. If a firewall is config to allow any communication from admin. So another person can spoof admin address to establish connection when it isn't the admin. So for example if someone has paid the fees of wifi and using it, one can change the mac address to the person to maybe establish connection.

## PING

Ping is the most fundamental tool available in networks. It uses ICMP(Internet Control Message Protocol) and checks the performance of the connection established. A echo packet present in the ICMP and the reply module is used to measure the transmission.

# LAN

* **STAR TOPOLOGY** - All the devices are connected with a central device like switch or hub and all the communication which happens within the devices go through the central device. This is the common topology found in today due to its *scalability*.

More cabiling is required for this topology and is quite expensive and if the central device fails it can stop all the communication but safely the central device is robust.

* **Bus topology** - This topology has a single backbone cable and all the data travels through that single cable to the device. Looks like a leaf from the branches. It is comparable cheaper to set up. Main problem is it can get bottlenecked if many devices try to request data. 

* **RING TOPOLOGY** - In this , devices like *computers are connected to each other forming a loop. This requires relatively less cable and less expensive than star topology, the data transmission happens between devices, so they can send the data they recieve first.Fairlyy easy to troubleshoot but is not that efficient as it travels through other devices before reaching its destination. If any cable is cut or disrupted it can disrupt the entire system.

## Switch

These are devices designed to connect various devices like computers, printers etc via ethernet. Found in schools, buisnesses. Much more efficient than hub, and it recognises what all devices are connected so it can send the data packets directly to the device requesting it.

One can connect switches and router with each other so that there is multiple path a data packet can take so that if one gets disrupted, other can be used.

**ROUTER** creates a path between network so that data transmission can happen, this process is called routing.

## Subnetting

Subnetting is a way of dividing network into smaller fragments and deciding who gets to own it. Network also needs to know where it is going, so network admins with the use of subnetting categorize the network divisions. Subnetting is done by limiting the number of hosts in a net, reps by a number called subnet mask.

Subnets uses ip address in three different ways:-

* Network address = This particular address shows the start of any network. For eg. device like 192.168.1.100 is to be located in the network 192.168.1.0

* Host address = like 192.168.1.100 etc

* Default gateway = this network is capable of establishing connection with other network.

Advantage is that it can make system efficient and divided accordingly.

## ARP

Address Resolution Protocol allows network to show themselves.

How ARP works:-

1. ARP requests = when this is done, a message is broadcasted in the whole server asking for the mac address of the given ip address.

2. ARP reply = then the device which owns that ip will reply with that MAC address. 

Then in future uses, the device then recognises this particular address and stores it in its ARP cache.

<mark>MAC is the physical identifier of the device and IP is the logical identifier of the device.</mark>

## DHCP

There are two ways of assigning IP address to a device, manually and by the use of DHCP(Dynamic host configuration protocol).

when a device connects to a network, if not already assigned, it sets out a **DHCP discover**, to see if any dhcp server is on the network, the dhcp server replies with a **dhcp offer**. the device then sends a **dhcp request** for getting the ip, the dhcp then sends a reply of **dhcp ack** that the process is completed.


# OSI Model

(Open systems interconnection) model. encapsulation when pieces of information is added.

1. Physical layer = Devices uses electrical signals to transfer data in 0s and 1s.

2. Data link layer = this is responsible for the physical addressing of the data transmission. every comp comes with a installed Network interface card(NIC) which has MAC addresses burned into it from the vendors.

3. Network layer - these layer act as a an re-assembly point of data chunks, routing determines the optimised path for data transfer. OSPF (Open Shortest Path First) and RIP (Routing Information Protocol), these protocols determine whether a path is shortest, reliable, functional etc.

4. Transport - When data is send across network it follows basically 2 protocols
    
    * TCP(transmission control protocol) - secure and reliable, remains in constant connection between two devices, performs a lot more process for reliability. If one chunk of data is not recived, entire data cannot be used, much slower than UDP as high amount of processes has to be performed.This is usually seen in file transfer, browsing etc. This is much useful here as it requires the data to be full.

    * UDP(User datagram protocol) - this is less advamced then tcp and there is no synchronisation between the two computers whether it has recived or not. This makes it much faster than tcp and doesnt require a constant connection between the devices. This is used where complete data is not required, like for protocols for finding devices like arp and dhcp and also video streaming.
    <mark> the degraded quality pixels is just lost pieces of data</mark>

5. Session layer- while a connection is established, a session gets started. This acts responsible for closing the connection if not used for a while, and also sets checkpoints so that if data gets lost only the newest data chunks need to be transported.

6. Presentation layer - this acts as a translator of data to and from from application layer. This also is where security encryption happens and in this layer, if a person sends a client an email, the client may have another email software but the contents inside it will be same.

7. Application layer - this is the layer we all are familiar with. the GUI used to interact and various protocols exist, to see the interaction we have with various services like browsing etc.


Packets and frames are small pieces of data that, when forming together, make a larger piece of information or message. However, they are two different things in the OSI model. 

A packet is a piece of data from Layer 3 (Network Layer) of the OSI model, containing information such as an IP header and payload. A frame, however, is used at Layer 2 (Data Link) of the OSI model, which, encapsulates the packet and adds additional information such as MAC addresses.

You can think of this process as similar to mailing a letter through the post. The envelope is a frame, which, is used to move the contents (in this analogy, the packet) of the envelope to another place. Once the recepient opens the envelop (frame), they will know how to forward the letter (packet) itself.

This process is called encapsulation which we discussed in room 3: the OSI model. At this stage, it's safe to assume that when we are talking about anything IP addresses, we are talking about packets. When the encapsulating information is stripped away, we're talking about the frame itself.

Packets are an efficient way of communicating data across networked devices such as those explained in Task 1. Because this data is exchanged in small pieces, there is less chance of bottlenecking occurring across a network than large messages being sent at once.

For example, when loading an image from a website, this image is not sent to your computer as a whole, but rather small pieces where it is reconstructed on your computer. Take the image below as an illustration of this process. The cat's picture is divided into three packets, where it is reconstructed when it reaches the computer to form the final image.

Packets have different structures that are dependant upon the type of packet that is being sent. As we'll come on to discuss, networking is full of standards and protocols that act as a set of rules for how the packet is handled on a device. With billions of devices connected on the internet, things can quickly break down if there is no standardisation.

Let's continue with our example of the Internet Protocol. A packet using this protocol will have a set of headers that contain additional pieces of information to the data that is being sent across a network.

Some notable headers include:
Header 	Description
Time to Live 	This field sets an expiry timer for the packet to not clog up your network if it never manages to reach a host or escape!
Checksum 	This field provides integrity checking for protocols such as TCP/IP. If any data is changed, this value will be different from what was expected and therefore corrupt.
Source Address 	The IP address of the device that the packet is being sent from so that data knows where to return to.
Destination Address 	The device's IP address the packet is being sent to so that data knows where to travel next.

TCP (or Transmission Control Protocol for short) is another one of these rules used in networking.


This protocol is very similar to the OSI model that we have previously discussed in room three of this module so far. The TCP/IP protocol consists of four layers and is arguably just a summarised version of the OSI model. These layers are:

    Application
    Transport
    Internet
    Network Interface


Very similar to how the OSI model works, information is added to each layer of the TCP model as the piece of data (or packet) traverses it. As you may recall, this process is known as encapsulation - where the reverse of this process is decapsulation.


One defining feature of TCP is that it is connection-based, which means that TCP must establish a connection between both a client and a device acting as a server before data is sent.


Because of this, TCP guarantees that any data sent will be received on the other end. This process is named the Three-way handshake, which is something we'll come on to discuss shortly. A table comparing the advantages and disadvantages of TCP is located below:


Advantages of TCP	Disadvantages of TCP
Guarantees the integrity of data.	Requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used and must be re-sent.
Capable of synchronising two devices to prevent each other from being flooded with data in the wrong order.	A slow connection can bottleneck another device as the connection will be reserved on the other device the whole time.
Performs a lot more processes for reliability	TCP is significantly slower than UDP because more work (computing) has to be done by the devices using this protocol.


TCP packets contain various sections of information known as headers that are added from encapsulation. Let's explain some of the crucial headers in the table below:


Header	Description
Source Port	This value is the port opened by the sender to send the TCP packet from. This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time).
Destination Port	This value is the port number that an application or service is running on the remote host (the one receiving data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random.
Source IP	This is the IP address of the device that is sending the packet.
Destination IP	This is the IP address of the device that the packet is destined for.
Sequence Number	When a connection occurs, the first piece of data transmitted is given a random number. We'll explain this more in-depth further on.
Acknowledgement Number	After a piece of data has been given a sequence number, the number for the next piece of data will have the sequence number + 1. We'll also explain this more in-depth further on.
Checksum	This value is what gives TCP integrity. A mathematical calculation is made where the output is remembered. When the receiving device performs the mathematical calculation, the data must be corrupt if the output is different from what was sent.
Data	This header is where the data, i.e. bytes of a file that is being transmitted, is stored.
Flag	This header determines how the packet should be handled by either device during the handshake process. Specific flags will determine specific behaviours, which is what we'll come on to explain below.


Next, we'll come on to discuss the Three-way handshake - the term given for the process used to establish a connection between two devices. The Three-way handshake communicates using a few special messages - the table below highlights the main ones:


Step	Message	Description
1	SYN	A SYN message is the initial packet sent by a client during the handshake. This packet is used to initiate a connection and synchronise the two devices together (we'll explain this further later on).
2	SYN/ACK	This packet is sent by the receiving device (server) to acknowledge the synchronisation attempt from the client.
3	ACK	The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received.
4	DATA	Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message.
5	FIN	This packet is used to cleanly (properly) close the connection after it has been complete.
#	RST	This packet abruptly ends all communication. This is the last resort and indicates there was some problem during the process. For example, if the service or application is not working correctly, or the system has faults such as low resources. 

The diagram below shows a normal Three-way handshake process between Alice and Bob. In real life, this would be between two devices.


Any sent data is given a random number sequence and is reconstructed using this number sequence and incrementing by 1. Both computers must agree on the same number sequence for data to be sent in the correct order. This order is agreed upon during three steps:

    SYN - Client: Here's my Initial Sequence Number(ISN) to SYNchronise with (0)
    SYN/ACK - Server: Here's my Initial Sequence Number (ISN) to SYNchronise with (5,000), and I ACKnowledge your initial number sequence (0)
    ACK - Client: I ACKnowledge your Initial Sequence Number (ISN) of (5,000), here is some data that is my ISN+1 (0 + 1)

Device
	Initial Number Sequence (ISN)	
	Final Number Sequence	
Client (Sender)	
	0	0 + 1 = 1
Client (Sender)	
	1	    1 + 1 = 2	
Client (Sender)	
	2	

2 + 1 = 3
TCP Closing a Connection:

Let's quickly explain the process behind TCP closing a connection. First, TCP will close a connection once a device has determined that the other device has successfully received all of the data.

Because TCP reserves system resources on a device, it is best practice to close TCP connections as soon as possible.

To initiate the closure of a TCP connection, the device will send a "FIN" packet to the other device. Of course, with TCP, the other device will also have to acknowledge this packet.

Let's show this process using Alice and Bob as we have previously.


In the illustration, we can see that Alice has sent Bob a "FIN" packet. Because Bob received this, he will let Alice know that he received it and that he also wants to close the connection (using FIN). Alice has heard Bob loud and clear and will let Bob know that she acknowledges this.

