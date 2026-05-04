# OSI model

open systems interconnection refernece model, to describe the process data takes as it traverses through the model.

Many protocols now follow TCP/IP protocols but osi can be applied to and can be worked with tcp/ip.

Individual layers can have many different protocol in it. This is a common language in IT industry.

Application, Presentation, Session, Transport, Network, Data link, Physical.

All people seem to need data processing.

## Layer 1 - physical layer

signals send through cables and fibres, not many protocols here, to and fro.

Problems can be , cable problem, test done like loopback tests, replace cables or swap cards.

## Layer 2 - data link

communicate between two devices on the lvel.

Data link control(DLC) protocols and MAC address on internet is the physical address. This is the hardware address not the os one.

Switching layer.

## Layer 3 - network layer.

Routing layer, routers determine how to forward traffic and looks at IP, fragement frames into multiple fragements and then put them back together in another device.

## Layer 4 - transport layer

transport from one device to another, post office layer.

TCP and UDP protocols are used here often.

## Layer 5 - session layer

before transport a session between two devices to be made.

Start stop restard, control and tunnelling protocols.

## Layer 6 - presentation layer.

Character encoding, encryption and combined with application layer.

## Layer 7 - application layer

we see this layer, HTTP, FTP , DNS these protocols exist in this.

## Real world into osi layers

layer 1 - cables, fibre and signals
layer 2 - frame, mac address, EXtended unique identifier(EUI-48, EUI-64)

layer 3- ip address

layer 4 tcp and udp

layer 5 control protocols to start session

layer 6 apps encryption SSL TLS

layer 7 what we see

Use wireshark to capture data and study.

# Networking device

## Router

allows a data in one ip subnet and take that into different ip subnet, maybe located next to each other or different parts of the world.

ip address is used to know where to send the data.

Layer 3 switches is the routers inside the switches.

## Firewalls

filters traffic on tcp/udp number - traditional

NGFW - latest.

Encrypts traffic through VPN and can create encrypted tunnels.

Firewalls can be a layer 3 devices, sits between ingress and egress as data goes into and out.  Internet traffic comes into the local network and firewall manages.

## IDS and IPS

intrusion detection system and prevention

mostly now this is integrated in modern new gen firewals, watches network traffic

Intrusions - exploits against op system, buffer overflows, cross-site scripting.

Detection - alarm or alert
Prevention - stop before it gets into the network.

## Balancing the load

Site uses a load balancer, and balances across multiple servers.

Web server farms and database farms in large scale..

Fault tolerance- load balanceer recognizes and takes the faulty server out and works smoothly.

TCP offload - protocol overhead and SSL offload - encryption decryption

CAching gives fast response.

Prioritization - Quality of Service(QoS)

Proxies - concern that user can communicate directly with the server.
proxies take the request and sends on their behalf, sits in middle and checks the query if there is no malicious content.

Useful for caching(fast), access control and url filtering.

## NAS v SAN

* NAS - connects to shared storage device across the network.
File-level access.

* SAN - feels like local storgae device.
Block level access.

## Access Point (AP)

a wireless router and a access point in a single device.

Access point is a bridge that extends wired network onto wireless network.
OSI layer 2 device.

Wireless networking is pervasive and dont have just a single access point.

Network should be invisible to users.

## Wireless LAN controller

a single device which can deploy new access point and see performance and security monitoring.
configure and deploy changes in sites and report on access point use.

# Networking Functions

Access to imp data, remmote access, traffic management.

## CDN(Content delivery network )

Speeds ip process of one data to another, Geographically distributed caching servers, so they duplicate the data and users get data from local server.

When using youtube its a content delivery network.

## VPN

* Secure data traversal in a public network, encrypted communication in insecure medium

* concentrator - encryption/decryption access device and integrated in firewall.

specialized cryptographic hardware(large-scale) and software based options(small-scale).

Sometimes built into OS like in linux.

## Quality of Service(QoS)

* high priorities and low priorites

Traffic shaping, packet shaping.

Control using bandwidth usage and set applications higher on imp applications.

* Qos managed with changes in config in routers, switches etc.

## Time to live(TTL)

* If task going on for too long, then it can be removed from network.

So a common way is to create a timer, number of times in traversees then stops.

Drop a packet caught in loop and clear a cache(in website the cache is stored for 60 secs for eg) then after that when u visit the website then again u have to load the website properly.

