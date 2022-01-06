# MitM-Spoofing-Attacks

## ARP Spoofing

There are 3 containers:
 - bob: an HTTP server
 - alice: a firefox container
 - eve: an eavesdropper/forger

### Attacking an HTTP Web Server

To run the PoC, follow the next steps on the corresponding container:

Alice: \\
 1. Connect to Alice firefox tab by connecting to `http://localhost:5800`.
 2. Request Bob's page by connecting to `http://bob`.

Eve: \\
 1. Find out the IP for Alice and Bob containers using `dig` or `ifconfig`.
 2. Use `arpspoof` twice to catch all the traffic going between Alice and Bob using `arpspoof -t <bob_ip> <alice_ip>` and `arpspoof -t <alice_ip> <bob_ip>`.
 3. Run `mitmproxy -m transparent -s /root/proxy.py` to modify the web page content.

Reload Bob's HTTP page to see the attack taking place.

To check that the ARP spoofing is efective, one can attach to Alice container with `docker exec -it mitm_alice` and run `arp -a`. The MAC addresses of both Bob and Eve will be the same.

## DNS Spoofing


## PoC ideas

 1. ARP Spoofing to attack an HTTP web server (modify the content of the page, get sensitive information).  
 2. ARP Spoofing to attack an HTTPS web server.
 3. DNS Spoofing to redirect a user to a malicious web page. 
