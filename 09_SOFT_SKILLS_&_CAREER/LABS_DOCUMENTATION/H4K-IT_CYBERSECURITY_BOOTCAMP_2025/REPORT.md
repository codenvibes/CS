
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

---

# Challenge Summary

## AI Solutions Portal Profile Peek (100 pts)

### Task
CloudPatron, a growing SaaS company, just launched a customer feedback portal where users can rate services and leave reviews. Internally, reviews are stored in a database and summarized on an admin dashboard. The development team used lightweight templating and stored queries to improve performance.

However, a last-minute deployment skipped the usual sanitization middleware due to “time constraints before demo day.” You're invited as a red team intern to test this feedback form for any unintended behavior or system exposure.

Explore the form. Is there a way to to see if the app is exploitable?

### Category: Web

### Description
Exploiting an insecure direct object reference (IDOR) vulnerability in a feedback portal to access another user's profile and discover a hidden flag.

### Tools Used

- Web browser
- Developer Tools (View Page Source)

### Methodology

1. **Initial Access: Visited login page** at `http://68.183.205.254:34658/login`
	![[Pasted image 20250723081134.png]]
	
2. **Registered a new user** at `/register`
	- **Username:** attacker
	- **Password:** attacker
	![[Pasted image 20250723081340.png]]
	
3. **Successfully Logged in** and was redirected to the dashboard at `/dashboard`
	![[Pasted image 20250723081528.png]]
	
4. **Clicked profile link** and noted the URL: `/profile?id=2`
	![[Pasted image 20250723081623.png]]
	
5. **Modified `id=2` to `id=1`** and accessed the admin’s profile
	![[{92782614-64A8-423C-A30E-6D82BEBE246A}.png]]
	![[{EF24814F-9414-4A9C-A292-F982E5C64B52}.png]]
	
6. **Inspected the page source** to locate the hidden flag
	![[Pasted image 20250723081739.png]]

### Flag Captured: `h4kit{broken_object_control_found_4bb42c8346d9}`

### Lessons Learned

- Never trust client-side input; always validate access server-side.
- IDOR vulnerabilities are often exploitable using sequential IDs.
- Viewing page source is essential when hunting for hidden content.

---

##### Name of the challenge

- **Category**: Web, Forensics, Reverse Engineering, etc.
- **Description**: Brief summary
- **Tools Used**: List of tools
- **Methodology**:
    - Step-by-step approach
    - Screenshots 
    - Commands used
- **Flag Captured**: `h4kit{flag_here}`
- **Lessons Learned**:

---
# Conclusion


