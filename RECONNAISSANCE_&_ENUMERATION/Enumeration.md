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


### Common Enumeration Techniques & Tools

| Type                    | Examples                            | Tools                     |
| ----------------------- | ----------------------------------- | ------------------------- |
| **NetBIOS/SMB**         | Get network shares, users, OS info  | `enum4linux`, `smbclient` |
| **SNMP**                | Extract network device info         | `snmpwalk`                |
| **DNS Enumeration**     | Discover subdomains, zone transfers | `dig`, `dnsrecon`         |
| **Port/Service Enum**   | Discover open ports, banners        | `nmap`, `netcat`          |
| **LDAP/AD Enumeration** | Find users/groups in AD             | `ldapsearch`, BloodHound  |
| **Web App Enum**        | Discover hidden pages/files         | `gobuster`, `dirb`        |


---

## References

https://tryhackme.com/room/attacktivedirectory