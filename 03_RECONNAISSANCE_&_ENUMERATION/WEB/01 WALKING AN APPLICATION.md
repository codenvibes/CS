Manually review a web application for security issues using only your browsers developer tools. Hacking with just your browser, no tools or scripts.

Here is a short breakdown of the in-built browser tools you will use:
- **View Source** - Use your browser to view the human-readable source code of a website.
- **Inspector** - Learn how to inspect page elements and make changes to view usually blocked content.
- **Debugger** - Inspect and control the flow of a page's JavaScript
- **Network** - See all the network requests a page makes.

---

## Exploring The Website

As a penetration tester, your role when reviewing a website or web application is to discover features that could potentially be vulnerable and attempt to exploit them to assess whether or not they are. These features are usually parts of the website that require some interactivity with the user.  
  
Finding interactive portions of the website can be as easy as spotting a login form to manually reviewing the website's JavaScript. An excellent place to start is just with your browser exploring the website and noting down the individual pages/areas/features with a summary for each one.

An example site review for the Acme IT Support website would look something like this:

| **Feature**             | **URL**               | **Summary**                                                                                                                                               |
| ----------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Home Page               | /                     | This page contains a summary of what Acme IT Support does with a company photo of their staff.                                                            |
| Latest News             | /news                 | This page contains a list of recently published news articles by the company, and each news article has a link with an id number, i.e. /news/article?id=1 |
| News Article            | /news/article?id=1    | Displays the individual news article. Some articles seem to be blocked and reserved for premium customers only.                                           |
| Contact Page            | /contact              | This page contains a form for customers to contact the company. It contains name, email and message input fields and a send button.                       |
| Customers               | /customers            | This link redirects to /customers/login.                                                                                                                  |
| Customer Login          | /customers/login      | This page contains a login form with username and password fields.                                                                                        |
| Customer Signup         | /customers/signup     | This page contains a user-signup form that consists of a username, email, password and password confirmation input fields.                                |
| Customer Reset Password | /customers/reset      | Password reset form with an email address input field.                                                                                                    |
| Customer Dashboard      | /customers            | This page contains a list of the user's tickets submitted to the IT support company and a "Create Ticket" button.                                         |
| Create Ticket           | /customers/ticket/new | This page contains a form with a textbox for entering the IT issue and a file upload option to create an IT support ticket.                               |
| Customer Account        | /customers/account    | This page allows the user to edit their username, email and password.                                                                                     |
| Customer Logout         | /customers/logout     | This link logs the user out of the customer area.                                                                                                         |

We will start taking a deeper look into some of the pages we have discovered in the next task.

---

## Viewing The Page Source

The page source is the human-readable code returned to our browser/client from the web server each time we make a request.

The returned code is made up of HTML ( HyperText Markup Language), CSS ( Cascading Style Sheets ) and JavaScript, and it's what tells our browser what content to display, how to show it and adds an element of interactivity with JavaScript.

For our purposes, viewing the page source can help us discover more information about the web application.

### How do I view the Page Source?

1. While viewing a website, you can right-click on the page, and you'll see an option on the menu that says View Page Source.
2. Most browsers support putting view-source: in front of the URL for example, **view-source:https://www.google.com/**
3. In your browser menu, you'll find an option to view the page source. This option can sometimes be in submenus such as developer tools or more tools.

###   

### Let's view some Page Source!

Try viewing the page source of the home page of the Acme IT Support website. Unfortunately, explaining everything you can see here is well out of the scope of this room, and you'll need to look into website design/development courses to understand it fully. What we can do, is pick out bits of information that are of importance to us.

  

At the top of the page, you'll notice some code starting with `<!--` and ending with `-->` these are comments. Comments are messages left by the website developer, usually to explain something in the code to other programmers or even notes/reminders for themselves. These comments don't get displayed on the actual webpage. This comment describes how the homepage is temporary while a new one is in development. View the webpage in the comment to get your first flag.

  

Links to different pages in HTML are written in anchor tags ( these are HTML elements that start with `<a` ), and the link that you'll be directed to is stored in the `href` attribute.

  

For example, you'll see the contact page link on line 31:

  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/ccc306acf34d0c83ffd18f33da1a5994.png)  

If you view further down the page source, there is a hidden link to a page starting with "secr", view this link to get another flag. You obviously wouldn't get a flag in a real-world situation, but you may discover some private area used by the business for storing company/staff/customer information.  
  
External files such as CSS, JavaScript and Images can be included using the HTML code. In this example, you'll notice that these files are all stored in the same directory. If you view this directory in your web browser, there is a configuration error. What should be displayed is either a blank page or a 403 Forbidden page with an error stating you don't have access to the directory. Instead, the directory listing feature has been enabled, which in fact, lists every file in the directory. Sometimes this isn't an issue, and all the files in the directory are safe to be viewed by the public, but in some instances, backup files, source code or other confidential information could be stored here. In this instance, we get a flag in the flag.txt file.  
  
Many websites these days aren't made from scratch and use what's called a framework. A framework is a collection of premade code that easily allows a developer to include common features that a website would require, such as blogs, user management, form processing, and much more, saving the developers hours or days of development.  
  
Viewing the page source can often give us clues into whether a framework is in use and, if so, which framework and even what version. Knowing the framework and version can be a powerful find as there may be public vulnerabilities in the framework, and the website might not be using the most up to date version. At the bottom of the page, you'll find a comment about the framework and version in use and a link to the framework's website. Viewing the framework's website, you'll see that our website is, in fact, out of date. Read the update notice and use the information that you find to discover another flag.

---

---

---

## References

https://tryhackme.com/room/walkinganapplication