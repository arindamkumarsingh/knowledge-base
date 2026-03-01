# Cyber Kill Chain

Inspired by military kill chain, CKC is a sec framework introduced by lockheed martin. aim is to aware organisations to defend against cyber attacks by understanding how they are conducted. 

1. Recon  - information gathering.
2. Weaponisation - attacker creats a payload to target system's vulnerabilities.
3. Delivery - sends the weaponised payload to the target.
4. Exploitation - Payload then exploits the vulnerability in the target's system.
5. Installation - enables the attacker to install a backdoor or malware to maintain **persistence** in the target's env.<mark>A malware tries to keep its footprint in the system, even after it restarts, for eg. if the malware install itself in the *startup registry* then it will persist.</mark>
6. Command & Control(C2) - now with the backdoor installed, the attacker controls the system.
7. Actions on objectives - now the attacker can fulfill its aim and objectives, like data stealing etc.

# Recon

Collects info on target's info. Divided into two types - passive and active

In passive recon, the attacker collects info without making any noise, like using OSINT. In active recon, the attacker cannot stay perfectly invisible and requires some kind of contact with target like social engineering.

### Passive Recon 

Eg. WHOIS and DNS database. WHOIS reveals contact info, reg dates, domain owners unless hidden by privacy extension. for dns database, it can reveal dns servers and public ip. Web scraping and crawling, social media recon and ofcourse **Google Dorking**.

### Active Recon

Network port scanning, can identify live hosts and services. vulnerability scanning to identify weakness.

## Countermeasures

having less public info exposure. limiting info on websites, social media acc and DNS records. WHOIS records to not reveal anynames and addresses. and add privacy add-ons for a cost. Sec team must monitor network logs actively to detect the attacks.

# Weaponisation

The payload can be made from scratch or be ready made. Some encryption can be made to evade detection and the payload can be hidden in files like pdf or ms word files.

### egs

from an email attachment to a USB everything can be weaponised. An exploit kit is a type of automated platform containing exploits. Easy to be made exploits. Not all documents can be weaponised, usually ms office documents contain malicious macros. if enabled it can execute the set of instructions.

After the file is ready, the attacker can craft a phishing email with malicious attachment, or a web page.

### Countermeasures

the user needs to be careful upon recieveing emails to check if there is an attachments, should know to inspect the emails source to check legitmacy. if email consists of encrypted zip file , the user must not rush to quench their curiosity.

disable unnecessary features, uninstall unnecessary software. Disable macros in office docs, or limit to trusted sources.

# Delivery

### EGS

* phishing emails - contains link or file to malicious downloads, filename like `invoice.pdf.exe` can trick the user unlike `program.exe`.

* spear phishing emails - resemebles legitimate communication from the  trusted source, can mimic the sender's name or address which seems legitmate.

* File-sharing platforms - upload files to file sharing services.

* malicious web links

* malvertising - show adv on legitmate web to redirect them to malicious page

* sms phising(smishing) - sends text messages with malicious links or instructions to download a malware.

* Social eng - convice a user to download a malicious program

* physical means - delivering a usb drive.

### Countermeasures 

User to be awared with safe browsing practices, phishing, and social eng attacks. after user training, email and web filtering to be the standard in orgs. web apps firewals(waf) to be used to block malicious files available in www. network monitoring is vital.


# Exploitation

###  EGS

straight-forward approach being targeting a password-based system. If pass is default or weak, it can be easy for the hackers to discover. attackers can use phishing to trick users into submitting the password.

software vuln cover both client and network service. only a matter of time new vulns are getting discovered and exploit code is written. sometimes the exploit code is written before the vendor is even aware that the product has a vuln hence zero-day exploit.

### Counter measures

MFA should be enabled, this prevents the attacker from gaining access even with the proper credentials.

Patch management is known to eradicate vuln and vuln scanning can help discover an inssecure ports etc. 

Intrusion Prevention systems(IPS) can play a significant rule in blocking exploit attempts by inspecting network traffic.

# Installation

### egs

regardless of the exploit, persistence is necessary, like creating scheduled tasks in ms windows or cron job in linux, modifying startup scripts etc. installing a new system in windows or linux is a good approach.sometimes attacker can take advantage of system's inbuilt tools like leg windows tools and binarirees called living-off-the-land binaries(LOLBinaries).

In some cases, the attackers need to download and execute additional payloads to fortify their access. For example, they might deploy a web shell after exploiting a web application. A web shell is a small script written in a programming language that is supported by the exploited server; it allows the attacker to execute operating system commands on the target via a web browser interface. Running a web shell over a standard protocol such as HTTPS will ensure they can log in to their target system while camouflaging their activity within HTTPS traffic.

### Counter measures

Endpoint Detection and Response(EDR) allows monitoring endpoints for suspicious activites like unusual process creation, modification etc.

Application allowlisting prevents execution of unauthorised apps and runs only selected trusted apps