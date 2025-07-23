
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

## AI Solutions Portal Profile Peek

### Category: Web
### Description
Exploiting an insecure direct object reference (IDOR) vulnerability in a feedback portal to access another user's profile and discover a hidden flag.
### Tools Used

- Web browser
- Developer Tools (View Page Source)

### Methodology
    
    1. **Visited login page** at `http://68.183.205.254:34658/login`
        
    2. **Registered a new user** (attacker/attacker) at `/register`
        
    3. **Logged in** and was redirected to the dashboard at `/dashboard`
        
    4. **Clicked profile link** and noted the URL: `/profile?id=2`
        
    5. **Modified `id=2` to `id=1`** and accessed the admin’s profile
        
    6. **Inspected the page source** to locate the hidden flag
        
- **Flag Captured**: `h4kit{broken_object_control_found_4bb42c8346d9}`
    
- **Lessons Learned**:
    
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


