# Nmap

Knowledge is power - littlefinger

more true in case of hacking, info abt system, network or properly called enumeration.

For sec audits, IP is given, to get the idea of landscape, to know what all services are running on the target.  like eg running a web server, Windows ADD controller. 

1. first stage is port scanning, when a network service is run, a port is opened to establish connection. port binds itself with the incoming network connection, some conventions exist as to what all port to be connected to the services. Network connnection is made between an open port to the server and a randomly selected port of my own computer. 

2. whenever an incoming packet arrives, it has the port no. information written, so routing is done and the packet is send to the destination.

3. ports lie on the transport layer.

Eg. How multiple tabs are running in the browser, convention is the https port is 443, so this remains the same, but different number of 16 bit numbers (0–65535), so they take a randomly high values.

Some of the ports are standard, HTTP webservice is port 80, and HTTPS 443, NETBIOS - 139, SMB - 445.

But in CTF settings, these ports can also get altered, so proper enumeration to be done on the target.

Nmap basically connects and sends packets to each of the port, and sends response based on how ports response, if its open closed or filtered(firewall).

### Why nmap?

because no other tools matches it in terms of sheer power, and functionality, it can even perform exploit directly so its the industry standard.

1024 ports are well known standard ports.

## SWITCHES

Use help or man page to know more about switches

`-sS` = Syn Scan

`sU` = Udp scan

`-O` = Os discovery

`-sV` = version of services

`-v` and `-vv`(use this one more) = verbosity to show enough info.

`-oA` = save the output in all formats available

`-oN` = save in normal format

`-oG` = grepable format

`-A` = aggressive

`--script=vuln` = to activate from vuln category script


## Scan type

TCP connect scans = `-sT`

SYN "half-open" scans = `-sS`

UDP scans = `-sU`

### TCP connect scans

TCP three way handshake, connecting terminal(the attacking machine) sends a TCP request to target server with SYN, then server acknowledges with packet of tcp response containing syn as well as ACK flag, then terminal sends the handshake by sending  tcp request with ack flag set.

So if nmap sends tcp req to a closed port, then it will response with RST(reset) flag, so this would mean that the port is closed.

if its open, the SYN/ACK flag set will be sent as a response, so this means the port is open.

but if port is open, but hidden behind a firewall, many firewalls are config, to simply drop the incoming packets, so we get no response of syn/ack or rst flag, so this would mean that the port is filtered.

RFC 9293 determines the behaviour for tcp protocol.

### SYN scans

syn scans are used to scan tcp port range of target or targets. they are sometime refered to as half open or stealth scans.

What happens is when, the attacker sends the req, SYn flag, then the server responds with syn/ack, now as explained above if the port is open that means it will give the syn/ack flag, so after that the attacker(client) sends the RST flag which is the reset flag, which literally means abort!!!. so the connection is never established but we know about the open port.

**Advantages** - 

* it can be used to bypass older Intrusion Detection system, as they look for a three  way handshake, no longer the case now with modern ids systems, but still called nowadays "stealth" scans

* SYN scans are often not logged by apps listening on open ports, as standard practice is of to log a connection when its established, stealthy....

* fast as third process is not done.

#### Disadvantage

* require sudo permission to work correctly in linux, syn scans require to make raw packets which lies in the root user.

* unstable services are brought down by the syn scans, so if a client has given its production environment.

If u have sudo permission, nmap runs syn scans by default if not then runs tcp connect without sudo permisson.

### UDP SCANS

udp connections are stateless, no handshake is performed just sends the packet to destination expecting it to reach. good for connections like file sharing, its lacks the acknowledgment part which makes it difficult and slower to run.

If no response from udp port, then its refered to as open or filtered, if it gets a udp response(unusual), then it is marked as open, double checks if still no response then marks it as open or filtered and nmap moves on, if it is sent to a closed udp port it sends out an icmp(ping) containing the msg that port is unreachable.

This difficulty in understanding whether the port is actually open, it takes more time. So, good practice to run commands like

```bash
nmap -sU --top-ports (number) <target>
```
### NULL, FIN and Xmas TCp port scanes

they are even stealthier than syn scan.

* NULL(`-sN`) scans when the tcp req is sent with no flags set at all,so with rfc, the target host shuld respond with rst if port is closed.

* FIN(`-sF`) scans, req is sent with a fin flag( again rst flag if the port is closed)

* Xmas(`-sX`) sents malform tcp packet and expects rst response for closed ports, blinks as a xmass tree when viewed in packet capture.
(PSH, URG and FIN)

If the port is open, the response is identical and similiar to udp scan.

Acc to RFC 793 it mandates that closed ports to respond with RST tcp packet and not respond for open ports, this is not the case always, in microsoft windows and other cisco network devices, they are known to respond with RST to any malform tcp packet regardless the port is open or not.

The goal here is firewall evasion, so many firewalls are configured to drop the incoming packets which consists syn flag, so it effectivelly bypass but many firewalls know these scan types so not 100 percent effective.

### ICMP netwrok scanning

nmap sends a icmp packet(ping) to each possible ip address, when it responds it marks as the ip being alive, it can give somewhat of a baseline.

```bash
nmap -sn ip.1-254 or ip 0/24 cidr notation
```
the hyphen - determines the range of ip address.

The -sn switch tells Nmap not to scan any ports -- forcing it to rely primarily on ICMP echo packets (or ARP requests on a local network, if run with sudo or directly as the root user) to identify targets. In addition to the ICMP echo requests, the -sn switch will also cause nmap to send a TCP SYN packet to port 443 of the target, as well as a TCP ACK (or TCP SYN if not run as root) packet to port 80 of the target.

## NSE

nmap scripting engine an addition to nmap. these primary writtenin lua prog language, automating scanning and exploits.

https://nmap.org/book/nse-usage.html

this is the extensive library

most common are

* safe

* intrusive 

* vuln - scanning a vuln

* exploit - exploit a vulnerability

* auth - bypass auhentication services

* brute - brute force credentials

* discovery - query running services for further info

### workatbility

`--script=safe` = this will run applicable safe scripts against the target.

multiple scripts can be run using commas.

https://nmap.org/nsedoc/

some scripts with arguments to be made

### To search for scripts

first is the nmap website and second is the local storage.

`/usr/share/nmap/scripts` = all nse scripts is stored here.

to search here

use the abvdirectory/script.db 

this is jsut a normal database just edited. we can user grep here to search for the script name or type we want

OR

we can use ls command then in the `/scripts/*ftp*`

this will show all the script names with this using wildcard.

## Firewall evasion

A comman firewall config to know to bypass. Winndows with its default firewall blocks all icmp packets, its a problem as nmap uses ping to establish the activity or know if ips are alive. so if the ping or icmp packets donot reach then it will consider the ip as dead so no bother scanning it at all.

to get around this, `-Pn` tells nmap to not bother pinging the host before scanning, so this will treat the target as alive always so it bypasses the icmp block, but the price is it takes a very long time to complete the scan.(as if the host is dead, it will still double check every ports specified)

https://nmap.org/book/man-bypass-firewalls-ids.html

* `-f` = fragements packets, making it less likely to be discovered by firewall/

* --scan-delay <time>ms = adds delay in the packets sent, evading any time based firewalls.

# Practical

Does target ip responds to ping = ping `<ip-address>`

```
22 packets transmitted, 0 received, 100% packet loss, time 21488ms
```

Q. to perform xmas scan in first 999 ports

```bash
nmap -sX -p<number> <ip-address>
```

here we get port 999 which means these many are open or filtered


https://nmap.org/book/

use this for entirity reference...

----