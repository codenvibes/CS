Various ways of discovering hidden or private content on a webserver that could lead to new vulnerabilities.

---

Firstly, we should ask, in the context of web application security, what is content? Content can be many things, a file, video, picture, backup, a website feature. When we talk about content discovery, we're not talking about the obvious things we can see on a website; it's the things that aren't immediately presented to us and that weren't always intended for public access.  
  
This content could be, for example, pages or portals intended for staff usage, older versions of the website, backup files, configuration files, administration panels, etc.  
  
There are three main ways of discovering content on a website which we'll cover. Manually, Automated and OSINT (Open-Source Intelligence).

---

## Manual Discovery

There are multiple places we can manually check on a website to start discovering more content. 

### Robots.txt

==**`robots.txt`** is a simple text file that websites use to give instructions to web crawlers (like Googlebot, Bingbot, or other search engine bots) about which pages or files they’re allowed or not allowed to crawl and index.==

It’s part of the **Robots Exclusion Protocol (REP)** — a standard for managing crawler access to your site.

**Key points about `robots.txt`:**
- 📍 **Location:** It must be placed in the root directory of your website. For example, `https://example.com/robots.txt`.
- ⚙️ **Syntax:** It uses simple rules like `User-agent` to specify which bot the rule applies to, and `Disallow` or `Allow` to tell bots what they can or can’t crawl.
- 🚫 **Purpose:** Common uses include blocking private areas (like `/admin/`), preventing indexing of duplicate content, or managing crawl budgets for large sites.
- ❗ **Limitations:** It’s not a security feature — it only _requests_ bots to stay away; it doesn’t prevent them from accessing the content if they choose to ignore the rules.

---

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
    

---

If you’d like, I can help you write or check a `robots.txt` for your own site — just say so!

The robots.txt file is a document that tells search engines which pages they are and aren't allowed to show on their search engine results or ban specific search engines from crawling the website altogether. It can be common practice to restrict certain website areas so they aren't displayed in search engine results. These pages may be areas such as administration portals or files meant for the website's customers. This file gives us a great list of locations on the website that the owners don't want us to discover as penetration testers.

Take a look at the robots.txt file on the Acme IT Support website to see if they have anything they don't want to list - To do this open Firefox on the AttackBox, and enter the url: [http://MACHINE_IP/robots.txt](http://machine_ip/robots.txt)[](https://lab_web_url.p.thmlabs.com/robots.txt) (_this URL will update 2 minutes from when you start the machine in task 1_)

---

---

---

## References

https://tryhackme.com/room/contentdiscovery