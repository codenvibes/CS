#HOW_THE_WEB_WORKS


**DNS** stands for **Domain Name System**. It's like the internet's phonebook.

DNS translates **domain names** (like `www.google.com`) into **IP addresses** (like `142.250.190.68`) that computers use to identify each other on the network.
Humans remember names like `example.com`, but computers talk using numbers (IP addresses). DNS makes it easier for us to browse the web without needing to memorize those numbers.

**How DNS works (basic steps):**
1. **You type a website URL** in your browser (`www.example.com`).
2. **Your computer asks a DNS server** to find the IP address of that domain.
3. **The DNS server responds** with the IP address.
4. **Your browser connects** to that IP address and loads the website.

Think of DNS like your phone's contacts list:
- You search for “Mom” (domain name).
- Your phone finds her number (IP address) and calls her.

---

## Domain Hierarchy
![]()
<img width="500" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/a168c8511887fff98a6944619c4b5259.png">


|                        |                                                                                                           |                                  |                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------- | --------------------------------------------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| TLD (Top-Level Domain) | The last part of a domain name (e.g., .com). Comes in two types: gTLD (Generic) and ccTLD (Country Code). | `.com`, `.org`, `.ca`, `.uk`     | There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain). gTLDs show domain purpose, ccTLDs indicate geography.                                                                                                                                                                                                                                      |
| Second-Level Domain    | The part directly left of the TLD. Represents the main name chosen during registration.                   | `tryhackme` in `tryhackme.com`   | Up to 63 characters. Only a-z, 0-9, and hyphens (-). Cannot start/end with hyphens or use consecutive hyphens.                                                                                                                                                                                                                                                                             |
| Subdomain              | Sits to the left of the Second-Level Domain. Can be used to create subdivisions of a site.                | `admin` in `admin.tryhackme.com` | A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). You can use multiple subdomains split with periods to create longer names, such as jupiter.servers.tryhackme.com. But the length must be kept to 253 characters or less. |

---

## DNS Record Types

|                  |     |
| ---------------- | --- |
| **A Record**     |     |
| **AAAA Record**  |     |
| **CNAME Record** |     |
| **MX Record**    |     |
| **TXT Record**   |     |

___

## What happens when you make a DNS request
<img width="400" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1724075620083.png">
1. When you request a domain name, your computer first checks its local cache to see if you've previously looked up the address recently; if not, a request to your Recursive DNS Server will be made.
2. A Recursive DNS Server is usually provided by your ISP, but you can also choose your own. This server also has a local cache of recently looked up domain names. If a result is found locally, this is sent back to your computer, and your request ends here (this is common for popular and heavily requested services such as Google, Facebook, Twitter). If the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers.
3. The root servers act as the DNS backbone of the internet; their job is to redirect you to the correct Top Level Domain Server, depending on your request. If, for example, you request [www.tryhackme.com](http://www.tryhackme.com/), the root server will recognise the Top Level Domain of .com and refer you to the correct TLD server that deals with .com addresses.
4. The TLD server holds records for where to find the authoritative server to answer the DNS request. The authoritative server is often also known as the nameserver for the domain. For example, the name server for [tryhackme.com](http://tryhackme.com/) is [kip.ns.cloudflare.com](http://kip.ns.cloudflare.com/) and [uma.ns.cloudflare.com](http://uma.ns.cloudflare.com/). You'll often find multiple nameservers for a domain name to act as a backup in case one goes down.
5. An authoritative DNS server is the server that is responsible for storing the DNS records for a particular domain name and where any updates to your domain name DNS records would be made. Depending on the record type, the DNS record is then sent back to the Recursive DNS Server, where a local copy will be cached for future requests and then relayed back to the original client that made the request. DNS records all come with a TTL (Time To Live) value. This value is a number represented in seconds that the response should be saved for locally until you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.


---

## References

https://tryhackme.com/room/dnsindetail