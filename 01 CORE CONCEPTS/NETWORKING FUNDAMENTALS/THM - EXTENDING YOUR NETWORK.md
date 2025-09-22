#THM-PRE_SECURITY #2-NETWORK_FUNDAMENTALS

## 1. Introduction to Port Forwarding

Port forwarding is an essential component in connecting applications and services to the Internet. Without port forwarding, applications and services such as web servers are only available to devices within the same direct network.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

==DEF-Port forwarding is a **networking technique** that allows external devices (from the internet) to access specific services or devices inside a private network.==

Port forwarding opens a “door” into your network.

Here’s the idea:
- Your **router** sits between the internet and your local devices (PCs, consoles, cameras, servers).
- By default, the router **blocks unsolicited inbound traffic** from the internet for security.
- **Port forwarding** tells the router:
    > “If someone from the internet tries to connect on this port number, send that traffic to this specific device inside my network.”

**Example: Security Camera Access**

Imagine you have a **Wi-Fi security camera** at home, and you want to check the live feed when you’re at work.
- The camera is connected to your home network and streams video on **port 8080**.
- From inside your house, you can watch the feed by typing `192.168.1.50:8080` in your browser.
- But when you’re outside (on mobile data or office Wi-Fi), that local IP address doesn’t work—it only exists inside your home network.

**Solution: Port Forwarding**
- You log into your router and set up a port forwarding rule:
    > “Forward all incoming traffic on port 8080 from the internet to the camera at 192.168.1.50:8080.”
- Now, if you type your home’s **public IP address** (like `73.25.120.44:8080`) from anywhere in the world, the router will forward that request directly to your camera.

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

Take the network below as an example. Within this network, the server with an IP address of "192.168.1.10" runs a webserver on port 80. Only the two other computers on this network will be able to access it (this is known as an intranet).
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/326ef12878c2f669ad2374dba3635a44.svg" alt=""></div>

If the administrator wanted the website to be accessible to the public (using the Internet), they would have to implement port forwarding, like in the diagram below:
<div align="center"><br><img width="900" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/eb63570eb9f31d26ebd8207ec08058bc.svg" alt=""></div>

With this design, Network #2 will now be able to access the webserver running on Network #1 using the public IP address of Network #1 (82.62.51.70).

It is easy to confuse port forwarding with the behaviours of a firewall (a technology we'll come on to discuss in a later task). However, at this stage, just understand that port forwarding opens specific ports (recall how packets work). In comparison, firewalls determine if traffic can travel across these ports (even if these ports are open by port forwarding).

Port forwarding is configured at the router of a network.
<div>
<br>
<br>
</div>

### Questions

##### What is the name of the device that is used to configure port forwarding?
router
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Firewalls 101

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Practical - Firewall
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. VPN Basics
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. LAN Networking Devices
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Practical - Network Simulator
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/extendingyournetwork