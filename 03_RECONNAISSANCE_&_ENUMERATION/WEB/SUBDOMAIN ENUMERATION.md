**Subdomain enumeration** is the process of identifying valid subdomains for a given domain.

---

## [[SSL TLS CERTIFICATES|OSINT - SSL/TLS Certificates]]

### Questions

#### What domain was logged on crt.sh at 2020-12-26?
store.tryhackme.com

![[Pasted image 20250704111225.png]]

---

## [[GOOGLE DORKING|OSINT - Search Engines]]

Search engines contain trillions of links to more than a billion websites, which can be an excellent resource for finding new subdomains. Using advanced search methods on websites like Google, such as the `site: filter`, can narrow the search results. For example, `site:*.domain.com -site:www.domain.com` would only contain results leading to the domain name domain.com but exclude any links to www.domain.com; therefore, it shows us only subdomain names belonging to domain.com.

Go to [Google](https://tryhackme.com/room/google.com) and use the search term `site:*.tryhackme.com -site:www.tryhackme.com`, which should reveal a subdomain for tryhackme.com; use that subdomain to answer the question below.

### Questions

#### What is the TryHackMe subdomain beginning with **S** discovered using the above Google search?
store.tryhackme.com

![[Pasted image 20250704112339.png]]

---

## DNS Bruteforce

---

## OSINT - Sublist3r

---

## Virtual Hosts

---

## References

https://tryhackme.com/room/subdomainenumeration