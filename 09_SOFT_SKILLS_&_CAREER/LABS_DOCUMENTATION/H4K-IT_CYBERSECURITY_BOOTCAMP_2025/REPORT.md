
<!--Cover Page-->

<div align="center">
<h2>NAME: TERRENCE MACHOGU KEGENGO</h2>
<h2>EMAIL: <a href="mailto:terrence.tech@proton.me">terrence.tech@proton.me</a></h2>
<h2>WEDNESDAY 23RD JULY 2025</h2>
<br>
<h1><b>H4K-IT CYBERSECURITY BOOTCAMP 2025 – CTF CHALLENGE REPORT</b></h1>
</div>



---

# Introduction

The H4K-IT Bootcamp Capture the Flag (CTF) Challenge, held from **July 17 to July 19, 2025**, was a practical, hands-on cybersecurity competition tailored for participants of **Cohort 3** of the H4K-IT Cybersecurity Bootcamp. With **63 teams** participating, the event simulated real-world cyber threats, requiring players to apply offensive and defensive skills to solve a series of security-related challenges across various domains such as web exploitation, network forensics, cryptography, and reverse engineering.

This report documents my approach, methodologies, tools used, and key takeaways from the CTF. It aims to provide both a reflection of my problem-solving techniques and a technical breakdown of the challenges I tackled. Additionally, the report highlights how this CTF contributed to my growth as a cybersecurity practitioner, aligning with the bootcamp’s objective to produce industry-ready talent through immersive learning.

---

<!--Table of Contents-->

---

# Detailed Walkthrough

## AI Solutions Portal Profile Peek (100 pts)

### Task
CloudPatron, a growing SaaS company, just launched a customer feedback portal where users can rate services and leave reviews. Internally, reviews are stored in a database and summarized on an admin dashboard. The development team used lightweight templating and stored queries to improve performance.

However, a last-minute deployment skipped the usual sanitization middleware due to “time constraints before demo day.” You're invited as a red team intern to test this feedback form for any unintended behavior or system exposure.

Explore the form. Is there a way to to see if the app is exploitable?

### Category: Web

### Tools Used

- Web browser (Chrome)
- Developer Tools (View Page Source)

### Methodology

1. **Initial Access: Visited login page** at `http://68.183.205.254:34658/login`
	![[Pasted image 20250723081134.png]]
	
2. **Registered a new user** at `/register`
	- **Username:** attacker
	- **Password:** attacker
	![[Pasted image 20250723081340.png]]
	
3. **Successfully Logged in** and was redirected to the dashboard at `/dashboard`
	The dashboard displayed a welcome message and a hyperlink labeled **"View your profile here."**
	![[Pasted image 20250723081528.png]]
	
4. **Clicked profile link** and noted the URL: `/profile?id=2`
	![[Pasted image 20250723081623.png]]
	
5. **==IDOR Exploitation==; Modified the URL parameter from `id=2` to `id=1` and accessed the admin’s profile
	![[{92782614-64A8-423C-A30E-6D82BEBE246A}.png]]
	![[{EF24814F-9414-4A9C-A292-F982E5C64B52}.png]]
	
6. **Inspected the page source** and found a hidden flag embedded in the HTML:
	![[Pasted image 20250723081739.png]]

### Flag Captured: `h4kit{broken_object_control_found_4bb42c8346d9}`

### Lessons Learned

- Never trust client-side input; always validate access server-side.
- IDOR vulnerabilities are often exploitable using sequential IDs.
- Viewing page source is essential when hunting for hidden content.


## CorpDocs (200 pts)

### Task
CorpDocs is a lightweight internal document management system used by CloudNova Inc. Employees can register, upload files, and view personal dashboards. There’s also an /admin panel that was intended to be accessible only to internal staff during development.

The admin interface was deployed behind a simple "role check," but developers forgot to enforce authentication at the route level. Instead, visibility was handled on the frontend through link hiding, assuming no user would guess the admin URL.

You’ve been invited to assess the system. Investigate whether it’s possible to reach privileged content without logging in as an admin.

### Category: Web

### Tools Used

- Web browser (Chrome)
- Gobuster
- SecLists wordlist (`common.txt`)

### Methodology

1. Visited the login page `http://68.183.205.254:34664/login`
	- Found standard login form.
	- Discovered a link to the registration page.
	![[Pasted image 20250723130131.png]]
	
2. User Registration
	Registered at `http://68.183.205.254:34664/register`
	- Username: `attacker`
	- Password: `attacker`
	![[Pasted image 20250723130304.png]]
	
3. Login & Dashboard Access
	Logged in successfully and confirmed the user role was **user**, not **admin**.
    ![[Pasted image 20250723130408.png]]
    
4. Directory Bruteforce with Gobuster
	Used Gobuster to enumerate directories:
	
```
┌──(mopsy㉿APHP)-[~/H4K-IT]
└─$ gobuster dir -u http://68.183.205.254:34664 -w ~/SecLists/Discovery/Web-Content/common.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://68.183.205.254:34664
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /home/mopsy/SecLists/Discovery/Web-Content/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/admin                (Status: 200) [Size: 542]
/dashboard            (Status: 302) [Size: 199] [--> /login]
/login                (Status: 200) [Size: 476]
/register             (Status: 200) [Size: 450]
Progress: 4746 / 4747 (99.98%)
===============================================================
Finished
===============================================================
```

5. Discovered `/admin` endpoint via bruteforce.
    
6. Accessed `http://68.183.205.254:34664/admin` directly.
	Contents of the page:
	![[Pasted image 20250723130931.png]]

### Flag Captured: `h4kit{admin_panel_not_restricted_0825a0215d83}`

### Lessons Learned

- **Front-end-only access control is insecure.**  
    Simply hiding admin links from the UI does not protect routes from direct access.
    
- **Always perform directory brute-forcing.**  
    Gobuster (or similar tools) can uncover hidden or unlinked routes like `/admin`.
    
- **Backend route protection is essential.**  
    Access control logic must be enforced on the server, not just in the client.


## DevPortal Ownership Override (200 pts)

### Task
CorpDocs is a lightweight internal document management system used by CloudNova Inc. Employees can register, upload files, and view personal dashboards. There’s also an /admin panel that was intended to be accessible only to internal staff during development.

The admin interface was deployed behind a simple "role check," but developers forgot to enforce authentication at the route level. Instead, visibility was handled on the frontend through link hiding, assuming no user would guess the admin URL.

You’ve been invited to assess the system. Investigate whether it’s possible to reach privileged content without logging in as an admin.

### Category: Web

### Tools Used

- Web browser (Chrome)
- Developer Tools / View Page Source

### Methodology

1. Visited the login page `http://68.183.205.254:34684/login`
	- Found standard login form.
	- Discovered a link to the registration page.
    ![[Pasted image 20250723134548.png]]

2. User Registration
	Registered at `http://68.183.205.254:34684/register`
	- Username: `attacker`
	- Password: `attacker
    ![[Pasted image 20250723134635.png]]

3. Access Dashboard
	- **Redirected to Dashboard:** `http://68.183.205.254:34684/dashboard`
	- Dashboard Links:
	    - **Edit Profile:** `/settings?id=3`
	    - **View Profile:** `/profile?id=3`
	![[Pasted image 20250723135120.png]]

4. Viewed the attacker's profile at `/profile?id=3`.
    ![[Pasted image 20250723135235.png]]

5. Modified the `id` parameter to `1` to access the admin profile.
    ![[Pasted image 20250723135335.png]]

6. Inspected the page source and discovered the flag in the `<footer>` tag.
	![[Pasted image 20250723135520.png]]

### Flag Captured: `h4kit{email_override_success_e2359b737f00}`

### Lessons Learned

- IDOR vulnerabilities occur when access control is not enforced server-side.
- Even non-visible HTML elements (e.g., `<small>` inside `<footer>`) may contain sensitive data.
- Parameter tampering remains a common and dangerous flaw in web applications.


## Challenge

### Task

### Category: Web

### Tools Used

### Methodology

### Flag Captured: 

### Lessons Learned



## Challenge

### Task

### Category: Web

### Tools Used

### Methodology

### Flag Captured: 

### Lessons Learned



---

# Challenge Summary


---
# Conclusion



so the first page on launch is the login page http://68.183.205.254:34684/login and there's a link on the page to the registration page http://68.183.205.254:34684/register and I register username; attacker pass; attacker and login. the next page I get access to is the dashboard http://68.183.205.254:34684/dashboard and it looks like this;

## Welcome to your Dashboard

[Edit Profile](http://68.183.205.254:34684/settings?id=3) | [View Profile](http://68.183.205.254:34684/profile?id=3)


I click on view profile http://68.183.205.254:34684/profile?id=3 and get this; 

## Account Profile

**Username:** attacker

**Email:** attacker@mail.com


I switch the profile id to 1 http://68.183.205.254:34684/profile?id=1 and get this;

## Account Profile

**Username:** admin

**Email:** admin@dev.io

then view  page source and get this; 

```

<!DOCTYPE html>
<html>
<head><title>Profile – DevPortal</title><link rel="stylesheet" href="/static/style.css"></head>
<body>
<div class="container">
    <h2>Account Profile</h2>
    <p><strong>Username:</strong> admin</p>
    <p><strong>Email:</strong> admin@dev.io</p>
    
    <footer><small style="font-size: 0.1px;">h4kit{email_override_success_e2359b737f00}</small></footer>
    
</div>
</body>
</html>
```