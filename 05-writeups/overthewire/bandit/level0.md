# SSH

ssh is one of the most common cryptographic network protocol to securely connect from your own unsecured computer to another.

>IF you log into tryhackme machines you will be given three creds:
>> IP Address, username, password

**Syntax for logging using ssh**

```bash
ssh -p xx user@host
```
```bash
ssh username@ipaddress
```

`-p` stands for port, as various port will be open for your device to connect with it.

<mark>While using the online labs, be sure to use openvpn(open source vpn) as this is the most convienent way</mark>

## FActs

SSh was designed as replacement for telnet in unix-like systems.

Telnet and remote shell(before ssh) did not use any encryption so all the data and credentials would be visible to third party.

SSH uses cryptographic encryptions to encrypt transmissions which happens from one computer to another.

Many versions were released most common used is OpenSSH, the open source version developed by OpenBSD.

Works on three layers: 

*