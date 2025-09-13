#THMLP-JR_PENETRATION_TESTER #THMMOD-NETWORK_SECURITY

## 1. Introduction

In the first room of the Network Security Module, we focused on [passive reconnaissance](https://tryhackme.com/jr/passiverecon). In this second room, we focus on active reconnaissance and the essential tools related to it. We learn to use a web browser to collect more information about our target. Moreover, we discuss using simple tools such as `ping`, `traceroute`, `telnet`, and `nc` to gather information about the network, system, and services.

As we learned in the previous room, passive reconnaissance lets you gather information about your target without any kind of direct engagement or connection. You are watching from afar or checking publicly available information.

Active reconnaissance requires you to make some kind of contact with your target. This contact can be a phone call or a visit to the target company under some pretence to gather more information, usually as part of social engineering. Alternatively, it can be a direct connection to the target system, whether visiting their website or checking if their firewall has an SSH port open. ==Think of it like you are closely inspecting windows and door locks.== Hence, it is essential to remember not to engage in active reconnaissance work before getting signed legal authorization from the client.

In this room, we focus on active reconnaissance. Active reconnaissance begins with direct connections made to the target machine. Any such connection might leave information in the logs showing the client IP address, time of the connection, and duration of the connection, among other things. However, not all connections are suspicious. It is possible to let your active reconnaissance appear as regular client activity. Consider web browsing; no one would suspect a browser connected to a target web server among hundreds of other legitimate users. You can use such techniques to your advantage when working as part of the red team (attackers) and don’t want to alarm the blue team (defenders).

In this room, we go through various tools commonly bundled with most operating systems or easily obtainable. We begin with the web browser and its built-in developer tools; furthermore, we show you how a web browser can be “armed” to become an efficient reconnaissance framework. Afterwards, we discuss other benign tools such as `ping`, `traceroute`, and `telnet`. All these programs require connection to the target, and hence our activities would fall under active reconnaissance.

This room is of interest to anyone who wants to become familiar with essential tools and see how they can use them in active reconnaissance. The web browser developer tools might take some effort to gain familiarity, although it offers a graphical user interface. The command-line tools covered are relatively straightforward to use.

_**Important Notice**: Please note that if you're not subscribed, the AttackBox won't have Internet access, so you will need to use the VPN to complete the questions that require Internet access._
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Web Browser

The web browser can be a convenient tool, especially that it is readily available on all systems. There are several ways where you can use a web browser to gather information about a target.

On the transport level, the browser connects to:

- TCP port 80 by default when the website is accessed over HTTP
- TCP port 443 by default when the website is accessed over HTTPS

Since 80 and 443 are default ports for HTTP and HTTPS, the web browser does not show them in the address bar. However, it is possible to use custom ports to access a service. For instance, https://127.0.0.1:8834/ will connect to 127.0.0.1 (localhost) at port 8834 via HTTPS protocol. If there is an HTTPS server listening on that port, we will receive a web page.

While browsing a web page, you can press `Ctrl+Shift+I` on a PC or `Option + Command + I` (`⌥ + ⌘ + I`) on a Mac to open the Developer Tools on Firefox. Similar shortcuts will also get you started with Google Chrome or Chromium. Developer Tools lets you inspect many things that your browser has received and exchanged with the remote server. For instance, you can view and even modify the JavaScript (JS) files, inspect the cookies set on your system and discover the folder structure of the site content.

Below is a screenshot of Firefox Developer Tools. Chrome DevTools is quite similar.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/02722e27a2e85fa803c2baa52ab54fdf.png)

There are also plenty of add-ons for Firefox and Chrome that can help in penetration testing. Here are a few examples:

- **FoxyProxy** lets you quickly change the proxy server you are using to access the target website. This browser extension is convenient when you are using a tool such as Burp Suite or if you need to switch proxy servers regularly. You can get FoxyProxy for Firefox from [here](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard).
- **User-Agent Switcher and Manager** gives you the ability to pretend to be accessing the webpage from a different operating system or different web browser. In other words, you can pretend to be browsing a site using an iPhone when in fact, you are accessing it from Mozilla Firefox. You can download User-Agent Switcher and Manager for Firefox [here](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher).
- **Wappalyzer** provides insights about the technologies used on the visited websites. Such extension is handy, primarily when you collect all this information while browsing the website like any other user. A screenshot of Wappalyzer is shown below. You can find Wappalyzer for Firefox [here](https://addons.mozilla.org/en-US/firefox/addon/wappalyzer).

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/d8db9b9e278502db5ae2a6c12e79d890.png)

Over time, you might find a few extensions that fit perfectly in your workflow.
<div>
<br>
<br>
</div>

### Questions

##### 
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Ping
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Traceroute
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Telnet
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Netcat
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 7. Putting It All Together
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/activerecon