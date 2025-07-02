To summarise, when you request a website, your computer needs to know the server's IP address it needs to talk to; for this, it uses DNS. Your computer then talks to the web server using a special set of commands called the HTTP protocol; the webserver then returns HTML, JavaScript, CSS, Images, etc., which your browser then uses to correctly format and display the website to you.

![[Pasted image 20250702235202.png]]

There are also a few other components that help the web run more efficiently and provide extra features.

---

## Other Components
### Load Balancer

==A **load balancer** is a system or device that distributes incoming network traffic across multiple servers or resources to ensure no single server becomes overwhelmed.==

When a website's traffic starts getting quite large or is running an application that needs to have high availability, one web server might no longer do the job. Load balancers provide two main features, ensuring high traffic websites can handle the load and providing a failover if a server becomes unresponsive.

When you request a website with a load balancer, the load balancer will receive your request first and then forward it to one of the multiple servers behind it. The load balancer uses different algorithms to help it decide which server is best to deal with the request. A couple of examples of these algorithms are **round-robin**, which sends it to each server in turn, or **weighted**, which checks how many requests a server is currently dealing with and sends it to the least busy server.

Load balancers also perform periodic checks with each server to ensure they are running correctly; this is called a **health check**. If a server doesn't respond appropriately or doesn't respond, the load balancer will stop sending traffic until it responds appropriately again.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/829e340231cd8aa9f5ed2fa5c464ea80.svg)  

### CDN (Content Delivery Networks)

A **CDN** (Content Delivery Network) is a network of geographically distributed servers that work together to deliver web content (like images, videos, scripts, or entire web pages) to users **more quickly and reliably**.

**Here’s how it works:**
- Instead of serving content from a single origin server (like the one where your website is hosted), a CDN stores cached copies of your content on servers all over the world — these are called **edge servers**.
- When a user visits your website, the CDN delivers the content from the **edge server that’s physically closest to them**, which reduces latency and speeds up load times.
- CDNs also help handle **traffic spikes** by distributing requests across many servers, improving reliability and availability.

**Examples of popular CDNs:**
- Cloudflare
- Akamai
- Amazon CloudFront
- Google Cloud CDN
- Fastly

### Databases  

Often websites will need a way of storing information for their users. Webservers can communicate with databases to store and recall data from them. Databases can range from just a simple plain text file up to complex clusters of multiple servers providing speed and resilience. You'll come across some common databases: MySQL, MSSQL, MongoDB, Postgres, and more; each has its specific features.

### WAF (Web Application Firewall)

A **WAF** (Web Application Firewall) is a security system that **monitors, filters, and blocks** malicious HTTP/HTTPS traffic to and from a web application.

A WAF sits between your web request and the web server; its primary purpose is to protect the webserver from hacking or denial of service attacks. It analyses the web requests for common attack techniques, whether the request is from a real browser rather than a bot. It also checks if an excessive amount of web requests are being sent by utilising something called rate limiting, which will only allow a certain amount of requests from an IP per second. If a request is deemed a potential attack, it will be dropped and never sent to the webserver.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/24cb6468b4e51e8d8bbe7872e96a22b3.svg)

---

---

## References

https://tryhackme.com/room/puttingitalltogether