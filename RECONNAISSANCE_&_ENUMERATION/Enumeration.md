**Enumeration** is the process of **actively gathering detailed information about a target system or network**, usually after initial reconnaissance. It's a key phase in ethical hacking, penetration testing, and cybersecurity assessments.

During enumeration, an attacker or ethical hacker:

- Makes **active connections** to the target.
- Tries to **extract information** like:
    - Usernames
    - Group names
    - Network shares
    - Open ports
    - Running services
    - OS details
    - System banners

Basic enumeration starts out with an **nmap scan**. Nmap is a relatively complex utility that has been refined over the years to detect what ports are open on a device, what services are running, and even detect what operating system is running. It's important to note that not all services may be deteted correctly and not enumerated to it's fullest potential. Despite nmap being an overly complex utility, it cannot enumerate everything. Therefore after an initial nmap scan we'll be using other utilities to help us enumerate the services running on the device.

---

## References

https://tryhackme.com/room/attacktivedirectory