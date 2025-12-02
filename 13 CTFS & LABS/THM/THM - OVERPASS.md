---
tags:
  - THM
link: https://tryhackme.com/room/overpass
description: What happens when some broke CompSci students make a password manager?
---
## Summary

| SECTION/TASK     | FLAG |
| ---------------- | ---- |
| Task 1. Overpass |      |

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 1. Overpass

What happens when a group of broke Computer Science students try to make a password manager?  
Obviously a _perfect_ commercial success!

There is a TryHackMe subscription code hidden on this box. The first person to find and activate it will get a one month subscription for free! If you're already a subscriber, why not give the code to a friend?

UPDATE: The code is now claimed.  
The machine was slightly modified on 2020/09/25. This was only to improve the performance of the machine. It does not affect the process.
<div>
<br>
<br>
</div>

### Questions

##### Hack the machine and get the flag in user.txt

```
┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ nmap -sV -sC -A -T4 -p- --min-rate 1000 -oN nmap.txt 10.65.152.254
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-02 07:14 EST
Nmap scan report for 10.65.152.254
Host is up (0.20s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 59:52:de:ab:a3:37:77:1f:6b:63:94:b3:ca:7f:04:ad (RSA)
|   256 1e:13:06:9f:e3:4d:71:50:2b:ba:d8:9b:7a:e8:13:24 (ECDSA)
|_  256 0e:68:d7:fa:57:99:22:6f:44:43:34:0e:3f:a3:5b:f0 (ED25519)
80/tcp open  http    Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Overpass
Device type: general purpose
Running: Linux 4.X
OS CPE: cpe:/o:linux:linux_kernel:4.15
OS details: Linux 4.15
Network Distance: 3 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   202.17 ms 192.168.128.1
2   ...
3   203.70 ms 10.65.152.254

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 89.15 seconds
```
<div>
<br>
</div>

##### Escalate your privileges and get the flag in root.txt
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

