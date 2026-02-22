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