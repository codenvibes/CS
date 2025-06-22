## Task 1: Cyber security

### What you'll learn

- How to support a client in a cyber security breach
- How to read web activity logs

### What you'll do

- Help a client determine the source of a data breach
- Answer questions to identify suspicious user activity

### Here is the background information on your task

A major news publication has revealed sensitive private information about Daikibo Industrials, our client. A production problem has caused its assembly lines to stop, threatening the smooth operation of supply chains relying on Daikibo’s products. The client suspects the security of their new status board may have been breached.

# Here is your task

In this task you will be joining our cyber security team. Your job is to:

1. Determine if the alleged breach could have happened from an attacker on the internet directly (i.e. no access to Daikibo's VPN).
2. Inspect a _web_requests.log_ file (listing only data from a period when the alleged attack has to have happened):
    - Try to spot suspicious requests
        - **Hint:** In the Resources section, you can find a diagram example of how to read the logs file
        - **Hint:** Look for longer sequences of user requests
        - **Hint:** Notice the order of requests from Login → to requests for the dashboard page's resources (styles, scripts, images, etc.) → to API requests for the actual statuses of the machines
        - **Hint:** How would you recognise if an automated request to the API happens at an exact interval of time (assume no such functionality is available in the dashboard)?
    - If you've identified such requests make sure to write down the ID of the user (it's part of the requests)

Here is how the _web_requests.log_ file is structured:

- There is a sequence of blocks of text divided by empty lines
- Each block represents the activity of a unique IP address (no 2 blocks have the same IP)
- The block starts with the IP address followed by a table of the requests made to Daikibo's telemetry dashboard (the dashboard lives in Daikibo's intranet) by the device with this IP address, sorted by time
- The IP addresses are from the internal Daikibo network and are static
- 1 block can represent 1 or multiple browsing sessions
- Sessions made on different dates require new logins
- There is **no continuous polling/pushing of data** between client and server - the users need to refresh the page to get the latest data
    - **Hint:** For an easier visual inspection, open up the file in a code editor like Sublime Text or Visual Studio Code, expand the window to the full width of your screen and decrease font size until no text breaks on a new line

When you believe you have completed the 2 tasks above, submit your work by taking a quick quiz to check your discoveries. Start the quiz by clicking 'Start your quiz' below. Good luck!

## Here are some resources to help you

---

## References

https://www.theforage.com/simulations/deloitte-au/cyber-c1e3