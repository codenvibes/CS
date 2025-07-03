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

---

---

---

## References

https://tryhackme.com/room/walkinganapplication