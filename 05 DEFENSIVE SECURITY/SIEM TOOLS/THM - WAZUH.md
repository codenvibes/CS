---
tags:
  - THM
description: Wazuh is a free, open source and enterprise-ready security monitoring solution for threat detection, integrity monitoring.
link: https://tryhackme.com/room/wazuhct
---
## Summary

| SECTION/TASK                                     | FLAG                                         |
| ------------------------------------------------ | -------------------------------------------- |
| Introduction                                     | 2015<br>Agent<br>Manager                     |
| Required: Deploy Wazuh Server                    | No answer needed                             |
| Wazuh Agents                                     | No answer needed<br>No answer needed<br><br> |
| Wazuh Vulnerability Assessment & Security Events |                                              |
| Wazuh Policy Auditing                            |                                              |
| Monitoring Logons with Wazuh                     |                                              |
| Collecting Windows Logs with Wazuh               |                                              |
| Collecting Linux Logs with Wazuh                 |                                              |
| Auditing Commands on Linux with Wazuh            |                                              |
| Wazuh API                                        |                                              |
| Generating Reports with Wazuh                    |                                              |
| Loading Sample Data                              |                                              |

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 1. Introduction

Welcome to a room showcasing the capabilities of the Wazuh EDR software solution. In this room, you can expect to learn the following things:

- What is an EDR and why are they useful solutions
- Where an EDR like Wazuh is used
- Accessing Wazuh
- Navigating Wazuh
- Learning about Wazuh rules and alerts
- Digesting logs to view specific events on devices including Linux and Windows
- How you can extend Wazuh using plugins and its API

Firstly, let's understand what EDR solutions are exactly. Endpoint detection and response (EDR) are a series of tools and applications that monitor devices for an activity that could indicate a threat or security breach. These tools and applications have features that include:

- Auditing a device for common vulnerabilities
- Proactively monitoring a device for suspicious activity such as unauthorised logins, brute-force attacks or privilege escalations
- Visualising complex data and events into neat and trendy graphs
- Recording a device's normal operating behaviour to help with detecting anomalies
  

==Created in 2015==, [Wazuh](https://wazuh.com/) is an open-source, freely available and extensive EDR solution. It can be used in all scales of environments. Wazuh operates on a management and agent module. Simply, a device is dedicated to running Wazuh named a manager, where the manager is responsible for managing agents installed on the devices you’d like to monitor. Let's look at this model in the diagram below:
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/4c008954c296fe1fbca005637af73ea1.png" alt=""></div>

_We can see logs from three Agents being sent to the Wazuh server._
<div>
<br>
<br>
</div>

### Questions

##### When was Wazuh released?
2015

##### What is the term that Wazuh calls a device that is being monitored for suspicious activity and potential security threats?
Agent

##### What is the term that Wazuh calls a device that is being monitored for suspicious activity and potential security threats?
Manager
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 2. Required: Deploy Wazuh Server

[Connect](https://tryhackme.com/access) to the TryHackMe network and deploy the Wazuh management server attached to this task and wait a **minimum of five minutes** before visiting the Wazuh server on [HTTP://MACHINE_IP](http://machine_ip/).

**If you load the Wazuh management server too early, it will say "Kibana Server is not ready yet" Please wait a few more minutes before refreshing the page and trying again.**

Once it has started, log in using the following credentials:

**Username:** wazuh (**make sure that this is lowercase!**)
**Password:** eYa0M1-hG0e7rjGi-lRB2qGYVoonsG1K

Select "**Global Tenant**" after successfully logging in. Refer to the animated gif below of the process if you are stuck.
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/e072a26a84886784f231585294f763dd.gif" alt=""></div>

**Note:** The questions within the tasks of this room **will expect the data stored on this Wazuh management server**, so it is vital that you are able to connect to this server before continuing.  

The Wazuh management server in this room will show the agents as being _disconnected_ - this is expected.
<div>
<br>
<br>
</div>

### Questions

##### Login to the Wazuh management server on [HTTP://MACHINE_IP](http://machine_ip/)[](https://machine_ip.p.thmlabs.com/) before proceeding with this room's tasks.
No answer needed
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 3. Wazuh Agents

Devices that record the events and processes of a system are called agents. Agents monitor the processes and events that take place on the device, such as authentication and user management. Agents will offload these logs to a designated collector for processing, such as Wazuh.

In order for Wazuh to be populated, agents need to be installed onto devices to log such events. Wazuh can guide you through the agent deployment process provided you fill out some pre-requisites such as::

- Operating System
- The address of the Wazuh server that the agent should send logs to (this can be a DNS entry or an IP address)
- What group the agent will be under - you can sort agents into groups within Wazuh if you wish

This wizard can be launched by navigating to the following location on the Wazuh server: **Wazuh -> Agents -> Deploy New Agent** as illustrated in this screenshot below:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/561a60f3973c417098e4381bc50f9252.png)  

Once you navigate to this display, the intuitive wizard will be available to you. I have shared screenshots of using the wizard to install Wazuh's agent on both Windows and Debian/Ubuntu. At stage 4, you are given a command to copy and paste to your clipboard which will install & configure the agent on the device that you wish to collect logs from.

**Installing the Wazuh agent on Windows:**

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/5729622f750cdd7185c094ad09ce70f8.png)  

**Installing the Wazuh agent on Debian/Ubuntu:** 

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/e50f510af70b7cd247e5623cbd5f7e31.png)
<div>
<br>
<br>
</div>

### Questions

##### Ensure that you are logged in to the Wazuh management server on [HTTPS://10.10.171.243](https://10.10.171.243/)
No answer needed

##### Navigate to the "Agents" tab by pressing **Wazuh** -> **Agents**
No answer needed

##### How many agents does this Wazuh management server manage?
2

##### What are the status of the agents managed by this Wazuh management server?
disconnected
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 4. Wazuh Vulnerability Assessment & Security Events

Wazuh’s Vulnerability Assessment module is a powerful tool that can be used to periodically scan an agent’s operating system for installed applications and their version numbers.

Once this information has been gathered, it is sent back to the Wazuh server and compared against a database of CVEs to discover potential vulnerabilities. For example, the agent in the screenshot below has a version of Vim that is vulnerable to **CVE-2019–12735**.
<div align="center"><br><img width="1200" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/1907912f601690e47d5e11d031461f4b.png" alt=""></div>

The vulnerability scanner module will perform a full scan when the Wazuh agent is first installed on a device and **must** be configured to run at a set interval then after (by default, this is set to 5 minute intervals when enabled) like so:
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/06c4394959f434bffd04a4a6618b576b.png" alt=""></div>

_Configuring the Wazuh management server to audit agents for vulnerabilities frequently (/var/ossec/etc/ossec.conf)_

Wazuh is capable of testing an agent’s configuration against certain rulesets to check for compliance. However, out of the box, it is arguably sensitive. Take, for example, this Linux host running the Wazuh agent. There have been a total of 769 events occurring that the system performs as part of its daily maintenance
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/55456a88291bf69e44a15e5a742faf1e.png" alt=""></div>

These frequent actions, such as removing files, are often detected as a security event. These events and the related severities are determined by Wazuh’s rulesets, which is something that we will come on to explore adjusting in another task.

We can analyze these events individually by selecting the event’s dropdown. You can sort events based upon various factors such as timestamp, tactics, or description.

Press enter or click to view image in full size
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/3a195f897882eee1b3151a3b5b167054.gif" alt=""></div>
<div>
<br>
<br>
</div>

### Questions

##### Ensure that you are logged in to the Wazuh management server on
No answer needed

##### Navigate to the Agents tab by pressing **Wazuh** -> **Agents** like so
No answer needed

##### Select the agent named “**AGENT-001**”
No answer needed

##### How many “Security Event” alerts have been generated by the agent “AGENT-001”?<br>**Note**: You will need to make sure that your time range includes the 11th of March 2022<br>To find this, click “Security events”, then change the date range to include at least March 11th, 2022, then you’ll have your answer:

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 5. Wazuh Policy Auditing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 6. Monitoring Logons with Wazuh
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 7. Collecting Windows Logs with Wazuh
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 8. Collecting Linux Logs with Wazuh
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 9. Auditing Commands on Linux with Wazuh
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 10. Wazuh API
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 11. Generating Reports with Wazuh
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Task 12. Loading Sample Data
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/wazuhct