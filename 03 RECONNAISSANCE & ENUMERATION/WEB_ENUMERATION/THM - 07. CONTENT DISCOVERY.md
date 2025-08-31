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

### Favicon

The favicon is a small icon displayed in the browser's address bar or tab used for branding a website.
 
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/42a556740d021fc3e7111a689dcadb28.png)

Sometimes when frameworks are used to build a website, a favicon that is part of the installation gets leftover, and if the website developer doesn't replace this with a custom one, this can give us a clue on what framework is in use. OWASP host a database of common framework icons that you can use to check against the targets favicon [https://wiki.owasp.org/index.php/OWASP_favicon_database](https://wiki.owasp.org/index.php/OWASP_favicon_database). Once we know the framework stack, we can use external resources to discover more about it (see next section).

#### Practical Exercise

On the AttackBox, open firefox and enter the url [https://static-labs.tryhackme.cloud/sites/favicon/](https://static-labs.tryhackme.cloud/sites/favicon/) here you'll see a basic website with a note saying "Website coming soon...", if you look at your tabs you'll notice an icon that confirms this site is using a favicon.

Viewing the page source you'll see line six contains a link to the images/favicon.ico file. 

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/1f1217249bf0edf74c8e6d0ba58bbc58.png)  

If you run the following command on the AttackBox, it will download the favicon and get its md5 hash value which you can then lookup on the  
[https://wiki.owasp.org/index.php/OWASP_favicon_database](https://wiki.owasp.org/index.php/OWASP_favicon_database).

```shell-session
user@machine$ curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
```

Note: This curl will fail on the AttackBox if you are a free user, in which case you should use a VM for this. If your hash ends with 427e then your curl failed, and you may need to try it again. You could also run this on Windows in PowerShell as shown below.  

```markup
PS C:\> curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico -UseBasicParsing -o favicon.ico
PS C:\> Get-FileHash .\favicon.ico -Algorithm MD5 
```

<div>
<br>
<br>
</div>

### Questions

##### What framework did the favicon belong to?
cgiirc

```shell
root@ip-10-10-86-179:~# curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1406  100  1406    0     0  28120      0 --:--:-- --:--:-- --:--:-- 28120
f276b19aabcb4ae8cda4d22625c6735f  -
```

![[Pasted image 20250831104154.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Manual Discovery - Sitemap.xml

### Sitemap.xml

Unlike the robots.txt file, which restricts what search engine crawlers can look at, the sitemap.xml file gives a list of every file the website owner wishes to be listed on a search engine. These can sometimes contain areas of the website that are a bit more difficult to navigate to or even list some old webpages that the current site no longer uses but are still working behind the scenes.
 
Take a look at the sitemap.xml file on the Acme IT Support website to see if there's any new content we haven't yet discovered: [http://10.10.127.158/sitemap.xml](http://10.10.127.158/sitemap.xml)[](http://10.10.127.158/sitemap.xml) (open this in the FireFox browser on the AttackBox).
<div>
<br>
<br>
</div>

### Questions

##### What is the path of the secret area that can be found in the sitemap.xml file?
/s3cr3t-area

![[Pasted image 20250831111227.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Manual Discovery - HTTP Headers

When we make requests to the web server, the server returns various HTTP headers. These headers can sometimes contain useful information such as the webserver software and possibly the programming/scripting language in use. In the below example, we can see the webserver is NGINX version 1.18.0 and runs PHP version 7.4.3. Using this information, we could find vulnerable versions of software being used. Try running the below curl command against the web server, where the **-v** switch enables verbose mode, which will output the headers (there might be something interesting!).

```shell-session
user@machine$ curl http://10.10.127.158 -v
*   Trying 10.10.127.158:80...
* TCP_NODELAY set
* Connected to 10.10.127.158 (10.10.127.158) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.10.127.158
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< X-Powered-By: PHP/7.4.3
< Date: Mon, 19 Jul 2021 14:39:09 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
```
<div>
<br>
<br>
</div>

### Questions

##### What is the flag value from the X-FLAG header?
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