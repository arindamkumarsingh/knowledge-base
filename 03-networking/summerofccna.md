from one network traffic goes to the router to another network. Router directs the traffic.

Wireless Access Point(WAP) - Takes the network and broadcast it over the air, so the device can join in.

# switch

Switch lets devices on a local network talk to each other intelligently.

Connects terminal, office pcs, printers together in same network, with switch they can communicate fast and cleanly.

Before the switch there was hub, when one device sends data through hub, everyone gets it. So inefficient.

Switch sends the traffic to the designated place.

Switch has mental table which shows which device is connected  to which port.

Content Addressable Memory(CAM) table. Switch watches the incoming traffic and looks for the source MAC address and then stores the info of the address as well as which port it uses.

A switch operates at layer 2 of osi model, takes care of mac addresses.

When we ping an ip, it isnt about layer 3 but the layer 2 about mac and it all takes that. The layer 2 traffic are known as frames. and at layer 3 it becomes packet.

REAL WORLD TIP: On the job, if a device can’t reach another device on the same LAN, one of the first places I want to look is the switch’s MAC address table. If the switch hasn’t learned the device, that tells me something is wrong at the physical or data link level, cable, port, NIC, VLAN, something in that world.

Now while wireless is amazing but it also broadcast itself in the whole network and everyone can see it. So still wired are more reliable.

# Router

Helps to talk between different networks

10.1.1.x and 23.227.38.x

different network resides in different ip addresses group. So to communicate between these network group router paves its way.

So a switch cares more about its MAC addresses are like physical label of the neighbourhood. Router takes care of the ip addresses which gives the full map of the address.

Its not that router is better than switch its just that they are doing different jobs.

## gateways

Default gateway is the router interface in the local network. So whenever some data has to travel outside the network, we just redirect the traffic to router and router knows what to do.

Decision making happens constantly- If its local, then it uses ARP- Address Resolution Protocol to discover MAC address, if its not local then it discovers the MAC address of router.

REAL WORLD TIP: When a device can reach local machines but not the internet, one of the first things I check is the default gateway. Wrong gateway, missing gateway, or a gateway that’s down will break off-network communication fast. You’ll look like a wizard for spotting it early, but really you’re just understanding how routing actually works.

# TCP/IP 

Device talking to each other is not a natural occuring tech, we have invented that. Early companies had their own copmputer and build their own ways for the computers to communicate, so different vendor's deviec wouldnt be able to communicate.

These network systems early on were proprietary which worked for the company's products only.]

Needed to make a common standards of rules which everyone aggreed.

That model won was TCP/IP but the terminology or for better understanding the osi model won gives more clean explanation..

Whenever troubleshooting u always go layerwise.

### Encapsulation

Procoess of taking data from one layer and wrapping it into the layers own info before handling down the next layer.

A switch sees the destination mac address of the layer and forwards to correct one and router peels the layer 2 info, and looks inside layer 3 about the ip address and sends the packer.

Now since IP address is the ssame for destination, the router re-encapsulate the packet into a brand new frame with new source(router) and new destination MAC address for the next hop

<mark> MAC addresses change hop-by-hop.</mark>

When the frame goes to the web server, it first checks layer 2, checks the mac address, approves it, de-encapsulates and checks layer 3 , checks the ip address, approves it, then layer 4, sees TCP, port 443, belongs to secure web service, then finally the request reaches the application layer.

So the server reads the request, builds a response, and then the whole process happens again in reverse, encapsulate, send, route, switch, receive, de-encapsulate.

Before sending the data, TCP does the three way handshake, then after the data is send then it agrees for data.

TCP = reliability and UDP = spped

when video streaming is done, udp takes its role, if some chunk is gone then still it better to keep moving.
