#THM_JR_PENETRATION_TESTER #INTRODUCTION_TO_WEB_HACKING 

## 1. What Is Content Discovery?

Firstly, we should ask, in the context of web application security, what is content? Content can be many things, a file, video, picture, backup, a website feature. When we talk about content discovery, we're not talking about the obvious things we can see on a website; it's the things that aren't immediately presented to us and that weren't always intended for public access.  
  
This content could be, for example, pages or portals intended for staff usage, older versions of the website, backup files, configuration files, administration panels, etc.  
  
There are three main ways of discovering content on a website which we'll cover. Manually, Automated and OSINT (Open-Source Intelligence).  
  
Start the AttackBox (by clicking the blue "Start AttackBox" button), and the machine on this task.
<div>
<br>
<br>
</div>

### Questions

##### What is the Content Discovery method that begins with M?
Manually
<div>
<br>
</div>

##### What is the Content Discovery method that begins with A?
Automated
<div>
<br>
</div>

##### What is the Content Discovery method that begins with O?
OSINT
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Manual Discovery - Robots.txt

There are multiple places we can manually check on a website to start discovering more content. 

### Robots.txt

==**`robots.txt`** is a simple text file that websites use to give instructions to web crawlers (like Googlebot, Bingbot, or other search engine bots) about which pages or files they’re allowed or not allowed to crawl and index.==

It’s part of the **Robots Exclusion Protocol (REP)** — a standard for managing crawler access to your site.

**Key points about `robots.txt`:**
- 📍 **Location:** It must be placed in the root directory of your website. For example, `https://example.com/robots.txt`.
- ⚙️ **Syntax:** It uses simple rules like `User-agent` to specify which bot the rule applies to, and `Disallow` or `Allow` to tell bots what they can or can’t crawl.
- 🚫 **Purpose:** Common uses include blocking private areas (like `/admin/`), preventing indexing of duplicate content, or managing crawl budgets for large sites.
- ❗ **Limitations:** It’s not a security feature — it only _requests_ bots to stay away; it doesn’t prevent them from accessing the content if they choose to ignore the rules.


**Example `robots.txt`:**

```txt
User-agent: *
Disallow: /private/
Allow: /public/
```

This means:
- `User-agent: *` → applies to all bots.
- `Disallow: /private/` → bots should not crawl anything under `/private/`.
- `Allow: /public/` → bots can crawl `/public/`.


This file gives us a great list of locations on the website that the owners don't want us to discover as penetration testers.

Take a look at the robots.txt file on the Acme IT Support website to see if they have anything they don't want to list - To do this open Firefox on the AttackBox, and enter the url: [http://MACHINE_IP/robots.txt](http://machine_ip/robots.txt)[](https://lab_web_url.p.thmlabs.com/robots.txt) (_this URL will update 2 minutes from when you start the machine in task 1_)
<div>
<br>
<br>
</div>

### Questions

##### What is the directory in the robots.txt that isn't allowed to be viewed by web crawlers?
/staff-portal

![[Pasted image 20250703122229.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Manual Discovery - Favicon
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Manual Discovery - Sitemap.xml
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Manual Discovery - HTTP Headers
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Manual Discovery - Framework Stack
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 7. OSINT - Google Hacking / Dorking
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 8. OSINT - Wappalyzer
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 9. OSINT - Wayback Machine
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 10. OSINT - GitHub
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 11. OSINT - S3 Buckets
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 12. Automated Discovery
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/contentdiscovery