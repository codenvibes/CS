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

> Here’s how it works:
> - **`site:*.domain.com`** — This tells Google: _“Show me pages from any subdomain of `domain.com`.”_
>     - For example: `blog.domain.com`, `shop.domain.com`, `mail.domain.com`, etc.
>     - The `*` is a wildcard that matches any subdomain.
> - **`-site:www.domain.com`** — The minus sign means _“Exclude this.”_
>     - So, this part tells Google: _“Do not show pages from `www.domain.com`.”_
> 
> **Putting it all together:**  
> This search will show **only pages from subdomains of `domain.com`**, but it will leave out the main site at `www.domain.com`.
> So instead of getting links like `www.domain.com/home`, you might find:
> - `store.domain.com/products`
> - `support.domain.com/help`
> - `beta.domain.com/login`

Go to [Google](https://tryhackme.com/room/google.com) and use the search term `site:*.tryhackme.com -site:www.tryhackme.com`, which should reveal a subdomain for tryhackme.com; use that subdomain to answer the question below.

### Questions

#### What is the TryHackMe subdomain beginning with **S** discovered using the above Google search?
store.tryhackme.com

![[Pasted image 20250704112339.png]]

---

## DNS Bruteforce

==**DEF-Bruteforce DNS Enumeration** is the process of automatically generating and testing large numbers of possible subdomain names for a given domain to identify which ones resolve to valid IP addresses.==
Because this method requires many requests, we automate it with tools to make the process quicker. In this instance, we are using a tool called dnsrecon to perform this. Click the "View Site" button to open the static site, press the "Run DNSrecon Request" button to start the simulation, and then answer the question below.

### Questions

#### What is the first subdomain found with the dnsrecon tool?



---

## OSINT - Sublist3r

---

## Virtual Hosts

---

## References

https://tryhackme.com/room/subdomainenumeration