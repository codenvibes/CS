The primary purpose of most types of security assessments is to find and confirm vulnerabilities are present, so we can work to `patch`, `mitigate`, or `remove` them. There are different ways and methodologies to test how secure a computer system is.

Some types of security assessments are more appropriate for certain networks than others. But they all serve a purpose in improving cybersecurity. All organizations have different compliance requirements and risk tolerance, face different threats, and have different business models that determine the types of systems they run externally and internally. Some organizations have a much more mature security posture than their peers and can focus on advanced red team simulations conducted by third parties, while others are still working to establish baseline security. Regardless, all organizations must stay on top of both legacy and recent vulnerabilities and have a system for detecting and mitigating risks to their systems and data.

---
## Vulnerability Assessment

`Vulnerability assessments` are appropriate for all organizations and networks. A vulnerability assessment is based on a particular security standard, and compliance with these standards is analyzed (e.g., going through a checklist).

A vulnerability assessment can be based on various security standards. Which standards apply to a particular network will depend on many factors. These factors can include industry-specific and regional data security regulations, the size and form of a company's network, which types of applications they use or develop, and their security maturity level.

Vulnerability assessments may be performed independently or alongside other security assessments depending on an organization's situation.

---
## Penetration Test

A pentest is a type of simulated cyber attack, and pentesters conduct actions that a threat actor may perform to see if certain kinds of exploits are possible.

The key difference between a pentest and an actual cyber attack is that the former is done with the full legal consent of the entity being pentested. Whether a pentester is an employee or a third-party contractor, they will need to sign a lengthy legal document with the target company that describes what they're allowed to do and what they're not allowed to do. As with a vulnerability assessment, an effective pentest will result in a detailed report full of information that can be used to improve a network's security.

### Pentests based on By Access Level:
| Type          | Pentester's Knowledge      | Simulates                   | Common Use Case                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------- | -------------------------- | --------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Black Box** | No prior knowledge         | External attacker           | Public-facing attack simulation | Black box pentesting is done with no knowledge of a network's configuration or applications. Typically a tester will either be given network access (or an ethernet port and have to bypass Network Access Control NAC) and nothing else (requiring them to perform their own discovery for IP addresses) if the pentest is internal, or nothing more than the company name if the pentest is from an external standpoint. This type of pentesting is usually conducted by third parties from the perspective of an external attacker. Often the customer will ask the pentester to show them discovered internal/external IP addresses/network ranges so they can confirm ownership and note down any hosts that should be considered out-of-scope. |
| **Grey Box**  | Limited/internal knowledge | Insider or compromised user | Balance of realism and depth    | Grey box pentesting is done with a little bit of knowledge of the network they're testing, from a perspective equivalent to an employee who doesn't work in the IT department, such as a receptionist or customer service agent. The customer will typically give the tester in-scope network ranges or individual IP addresses in a grey box situation.                                                                                                                                                                                                                                                                                                                                                                                             |
| **White Box** | Full system knowledge      | Internal audit              | Thorough security assessment    | White box pentesting is typically conducted by giving the penetration tester full access to all systems, configurations, build documents, etc., and source code if web applications are in-scope. The goal here is to discover as many flaws as possible that would be difficult or impossible to discover blindly in a reasonable amount of time.                                                                                                                                                                                                                                                                                                                                                                                                   |

### Pentests based on Scope/Target:

Often, pentesters specialize in a particular area. Penetration testers must have knowledge of many different technologies but still will usually have a specialty.

| Type                               | Description                                                                            | Example Targets                       |
| ---------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------- |
| **Network/Infrastructure Pentest** | Assess all aspects of a computer network (internal or external network infrastructure) | Routers, firewalls, workstations      |
| **Web Application Pentest**        | Assesses security of websites and web applications                                     | Login forms, APIs, session tokens     |
| **Mobile App Pentest**             | Focuses on mobile applications (iOS/Android)                                           | APK/IPA files, APIs, local storage    |
| **Cloud Pentest**                  | Evaluates cloud environments and configurations                                        | AWS S3, IAM roles, Azure storage      |
| **Wireless Pentest**               | Analyzes Wi-Fi networks and access points                                              | Access points, wireless clients       |
| **Social Engineering Pentest**     | Tests human factor by tricking users                                                   | Employees, helpdesks, phishing emails |
| **Physical Pentest**               | Checks physical security controls                                                      | Entry points, locks, USB ports        |

### Pentests based on Evasion/Stealth Techniques:
| Type               | Stealth Level | Detectable by Security Tools? | Typical Use Case                         |
| ------------------ | ------------- | ----------------------------- | ---------------------------------------- |
| **Non-Evasive**    | ❌ Low         | ✅ Yes                         | Test detection and response capabilities |
| **Evasive**        | ✅ High        | ❌ Rarely                      | Mimic stealthy real-world attackers      |
| **Hybrid Evasive** | ⚠️ Medium     | ⚠️ Sometimes                  | Mix of stealth and coverage              |


---

## References

https://academy.hackthebox.com/module/108/section/1160