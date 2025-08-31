#THM_JR_PENETRATION_TESTER #INTRODUCTION_TO_WEB_HACKING 

## 1. Brief

==DEF-Subdomain enumeration is the process of finding valid subdomains for a domain, but why do we do this? We do this to expand our attack surface to try and discover more potential points of vulnerability.==
  
We will explore three different subdomain enumeration methods: Brute Force, OSINT (Open-Source Intelligence) and Virtual Host.  
  
Start the machine and then move onto the next task.
<div>
<br>
<br>
</div>

### Questions

##### What is a subdomain enumeration method beginning with B?
Brute Force
<div>
<br>
</div>

##### What is a subdomain enumeration method beginning with O?
OSINT
<div>
<br>
</div>

##### What is a subdomain enumeration method beginning with V?
Virtual Host
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. OSINT - SSL/TLS Certificates

When an SSL/TLS (Secure Sockets Layer/Transport Layer Security) certificate is created for a domain by a CA (Certificate Authority), CA's take part in what's called "Certificate Transparency (CT) logs". These are publicly accessible logs of every SSL/TLS certificate created for a domain name. The purpose of Certificate Transparency logs is to stop malicious and accidentally made certificates from being used. We can use this service to our advantage to discover subdomains belonging to a domain, sites like [https://crt.sh](https://crt.sh/) offer a searchable database of certificates that shows current and historical results.

Go to [crt.sh](https://crt.sh/) and search for the domain name **tryhackme.com**, find the entry that was logged at **2020-12-26** and enter the domain below to answer the question.

### What are SSL/TLS certificates?

**SSL** (Secure Sockets Layer) and its successor **TLS** (Transport Layer Security) are cryptographic protocols that secure communication over a network (mainly the internet).

- **DEF-SSL/TLS certificates** are digital certificates issued by a Certificate Authority (CA).
- They verify that a website (or server) is who it claims to be and enable **HTTPS**, which encrypts data between your browser and the server.
- Technically, the certificate contains the website’s public key, the domain name it’s issued for, the CA’s signature, and metadata like expiry dates.

When you see `https://` and the 🔒 lock icon in your browser — that’s SSL/TLS at work.

When an SSL/TLS certificate is issued for a website by a Certificate Authority (CA), it gets recorded in something called a **Certificate Transparency (CT) log**.

These logs are public lists of all SSL/TLS certificates created for websites. The main reason for CT logs is to help catch fake or mistakenly issued certificates before they can be used for bad purposes.



### How are SSL/TLS certificates used in OSINT (Open Source Intelligence)?

In OSINT investigations, SSL/TLS certificates can reveal valuable information. Here’s how:

#### 1. Identify related domains

- Many websites share the same certificate (like subdomains: `mail.example.com`, `api.example.com`).
- Certificate fields (like the **Subject Alternative Name** or SAN) often list multiple domains — so you can discover infrastructure connections.

#### 2. Reveal ownership clues

- Certificates sometimes include organization names, email addresses, or locations in the subject or issuer fields.
- This can help attribute a site to a company or person.

#### 3. Track infrastructure

- Some attackers reuse certificates across multiple servers.
- Investigators can search **certificate transparency logs** (public records of all certificates issued) to spot suspicious patterns or find related malicious domains.

#### 4. Timeline and history

- Certificates have issue/expiry dates — this helps track when a domain was likely active or changed hands.
- You can correlate this with other events (like domain registration dates).

#### 5. Bypass privacy shields

- Even if WHOIS data is hidden with privacy services, certificates might still expose real organizational info.



### Common tools and sites for SSL/TLS OSINT

- **Censys**, **Shodan** — search engines for internet-connected devices & their certificates.
- **crt.sh** — searches Certificate Transparency logs.
- **Google Certificate Transparency** — logs issued certs.
- **OpenSSL** — to manually inspect certs.



### Example scenario

**Imagine you find a suspicious phishing domain:**

1. Look up its certificate on `crt.sh`.
2. Find all other domains using the same cert → more phishing domains.
3. Check the organization field → link to the attacker or company.
4. Check logs for older certs → see if they reused info elsewhere.

<div>
<br>
<br>
</div>

### Questions

##### What domain was logged on crt.sh at 2020-12-26?
store.tryhackme.com

![[Pasted image 20250704111225.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. OSINT - Search Engines
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. DNS Bruteforce
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. OSINT - Sublist3r
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Virtual Hosts
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/subdomainenumeration