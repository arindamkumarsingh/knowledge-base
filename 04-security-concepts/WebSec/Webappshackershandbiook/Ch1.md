#Web Apps

## Evolution

Earlier, WWW consisted only of *websites*, which were like info repos with static docs. Flow of info was one-way, server to client, and every user were treated the same info. 

Many security vulnerabilites were from the web server software and if any attacker tried to attacked, he would not gain access to sensitive info because it was already there.

But what an attacker can do is convert the attacked server, use its storage and bandwidth(uni or corporate networks) to distribute "**warez**".

**warez** = very old term for illegal pirated content hosted on other websites. So consisted of cracked games, movies, e-books etc.


---

Now there is two-way flow of info, registration, login and many more.

The most serious attacjs are against web apps that exposes sensitive data or gain access to back end systems.

For other orgs, DDos attacks are a critical event.

___

### This site is secure

Mostly, the web apps claim to be secure because they use SSL(Secure Socket Layer), 128-bit.

in site's certificate it is claimed, that various cryptographic method is used, many other organizations cite their compliance with Payment Card Industry(PCI) standards

But these are not true, as many vulnerabilities are found in maximum of the sites scanned. 

### Main security problem: Users can submit Arbitrary input

As client is outside the application's control, user can input arbitrary input, so appllication must assume that the input can be potentially malicious. So, steps must be there so that input cannot compromise the logic and behaviour.

Majority of the attacks in web apps happens when  some input is sent  that causes an unexpected event.

* Users can interfere with request parameters, cookies, HTTP headers etc.

* Changing the price of a productt transmitted in a hidden HTML to fraudulently purchase the product for a cheaper amount.

<mark> SSl does nothing to stop the attacker from submitting the crafted input</mark>

