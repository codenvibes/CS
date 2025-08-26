#THM_JR_PENETRATION_TESTER #INTRODUCTION_TO_WEB_HACKING

Manually review a web application for security issues using only your browsers developer tools. Hacking with just your browser, no tools or scripts.

Here is a short breakdown of the in-built browser tools you will use:
- **View Source** - Use your browser to view the human-readable source code of a website.
- **Inspector** - Learn how to inspect page elements and make changes to view usually blocked content.
- **Debugger** - Inspect and control the flow of a page's JavaScript
- **Network** - See all the network requests a page makes.

---

## Exploring The Website



---

## Viewing The Page Source



---

## Developer Tools - Inspector



---

## Developer Tools - Debugger


---

## Developer Tools - Network  

The network tab on the developer tools can be used to keep track of every external request a webpage makes. If you click on the Network tab and then refresh the page, you'll see all the files the page is requesting. 
 
Try doing this on the contact page; you can press the trash can icon to delete the list if it gets a bit overpopulated.
 
With the network tab open, try filling in the contact form and pressing the **Send Message** button. You'll notice an event in the network tab, and this is the form being submitted in the background using a method called AJAX. AJAX is a method for sending and receiving network data in a web application background without interfering by changing the current web page.
 
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/9ec0890f159397547950ea1822994443.png)  
 
Examine the new entry on the network tab that the contact form created and view the page the data was sent to in order to reveal a flag.

![[Pasted image 20250703100328.png]]

---

## References

https://tryhackme.com/room/walkinganapplication