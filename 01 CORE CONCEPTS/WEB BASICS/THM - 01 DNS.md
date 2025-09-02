#HOW_THE_WEB_WORKS

## 1. What is DNS?

DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers. Much like every house has a unique address for sending mail directly to it, every computer on the internet has its own unique address to communicate with it called an IP address. An IP address looks like the following 104.26.10.229, 4 sets of digits ranging from 0 - 255 separated by a period. When you want to visit a website, it's not exactly convenient to remember this complicated set of numbers, and that's where DNS can help. So instead of remembering 104.26.10.229, you can remember [tryhackme.com](http://tryhackme.com/) instead.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

==**DEF-DNS** stands for **Domain Name System**. It's like the internet's phonebook. DNS translates **domain names** (like `www.google.com`) into **IP addresses** (like `142.250.190.68`) that computers use to identify each other on the network.
Humans remember names like `example.com`, but computers talk using numbers (IP addresses). DNS makes it easier for us to browse the web without needing to memorize those numbers.==

**How DNS works (basic steps):**
1. **You type a website URL** in your browser (`www.example.com`).
2. **Your computer asks a DNS server** to find the IP address of that domain.
3. **The DNS server responds** with the IP address.
4. **Your browser connects** to that IP address and loads the website.

Think of DNS like your phone's contacts list:
- You search for “Mom” (domain name).
- Your phone finds her number (IP address) and calls her.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### Questions

##### What does DNS stand for?
Domain Name System
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Domain Hierarchy
<div align="center"><br><img width="600" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/a168c8511887fff98a6944619c4b5259.png"></div>
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

|                        |                                                                                            |                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------ | -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TLD (Top-Level Domain) | The last part of a domain name (e.g., .com).                                               | `.com`, `.org`, `.ca`, `.uk`     | There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain). Historically a gTLD was meant to tell the user the domain name's purpose; for example, a .com would be for commercial purposes, .org for an organisation, .edu for education and .gov for government. And a ccTLD was used for geographical purposes, for example, .ca for sites based in Canada, .co.uk for sites based in the United Kingdom and so on. Due to such demand, there is an influx of new gTLDs ranging from .online , .club , .website , .biz and so many more. For a full list of over 2000 TLDs [click here](https://data.iana.org/TLD/tlds-alpha-by-domain.txt). |
| Second-Level Domain    | The part directly left of the TLD. Represents the main name chosen during registration.    | `tryhackme` in `tryhackme.com`   | Up to 63 characters. Only a-z, 0-9, and hyphens (-). Cannot start/end with hyphens or use consecutive hyphens.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Subdomain              | Sits to the left of the Second-Level Domain. Can be used to create subdivisions of a site. | `admin` in `admin.tryhackme.com` | A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). You can use multiple subdomains split with periods to create longer names, such as jupiter.servers.tryhackme.com. But the length must be kept to 253 characters or less.                                                                                                                                                                                                                                                                                         |
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### Questions

##### What is the maximum length of a subdomain?
63
<div>
<br>
</div>

##### Which of the following characters cannot be used in a subdomain ( 3 b _ - )?
<div>
<br>
</div>

##### What is the maximum length of a domain name?
<div>
<br>
</div>

##### What type of TLD is .co.uk?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Record Types
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Making A Request
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Practical
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/dnsindetail