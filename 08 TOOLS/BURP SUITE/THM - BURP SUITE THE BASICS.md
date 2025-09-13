#THMLP-JR_PENETRATION_TESTER #THMMOD-BURP_SUITE #Burp_Suite

## 1. Introduction

#### Welcome to Burp Suite Basics!

This particular room aims to understand the basics of the Burp Suite web application security testing framework. Our focus will revolve around the following key aspects:

1. A thorough introduction to Burp Suite.
2. A comprehensive overview of the various tools available within the framework.
3. Detailed guidance on the process of installing Burp Suite on your system.
4. Navigating and configuring Burp Suite.

We will also introduce the core of the Burp Suite framework, which is the Burp Proxy. It is important to note that this room primarily serves as a foundational resource for acquiring knowledge about Burp Suite. Subsequent rooms in the Burp module will adopt a more practical approach. Thus, this room will contain a greater emphasis on theoretical content. If you have not yet utilised Burp Suite, it is recommended to carefully read the provided information and actively engage with the tool. Experimentation is essential for grasping the fundamentals of this framework. Combining the information presented here with hands-on exploration will establish a strong foundation for utilising the framework. This will significantly assist you in future rooms.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. What is Burp Suite

In essence, Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing. It has become the industry standard tool for hands-on security assessments of web and mobile applications, including those that rely on **a**pplication **p**rogramming **i**nterface**s** (APIs).

Simply put, Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. This fundamental capability forms the backbone of the framework. By intercepting requests, users have the flexibility to route them to various components within the Burp Suite framework, which we will explore in upcoming sections. The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

Burp Suite is available in different editions. For our purposes, we will focus on the **Burp Suite Community Edition**, which is freely accessible for non-commercial use within legal boundaries. However, it's worth noting that Burp Suite also offers Professional and Enterprise editions, which come with advanced features and require licensing:

1. **Burp Suite Professional** is an unrestricted version of Burp Suite Community. It comes with features such as:
    
    - An automated vulnerability scanner.
    - A fuzzer/brute-forcer that isn't rate limited.
    - Saving projects for future use and report generation.
    - A built-in API to allow integration with other tools.
    - Unrestricted access to add new extensions for greater functionality.
    - Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger-owned server).
    
    In short, Burp Suite Professional is a highly potent tool, making it a preferred choice for professionals in the field.
    
1. **Burp Suite Enterprise**, in contrast to the community and professional editions, is primarily utilized for continuous scanning. It features an automated scanner that periodically scans web applications for vulnerabilities, similar to how tools like Nessus perform automated infrastructure scanning. Unlike the other editions, which allow manual attacks from a local machine, Burp Suite Enterprise resides on a server and constantly scans the target web applications for potential vulnerabilities.
    ![Preview of Burp Suite Enterprise](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/6b7cdf06b365b6908c41525e8efb86e0.png)

Due to requiring a license for the Professional and Enterprise editions, we will focus on the core feature set provided by the Burp Suite Community Edition.

**Note:** The provided demonstrations utilize Burp Suite for Windows. However, the functionality remains consistent with the version installed on the AttackBox.
<div>
<br>
<br>
</div>

### Questions

##### Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?
Burp Suite Enterprise

##### Burp Suite is frequently used when attacking web applications and ______ applications.
Mobile
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Features of Burp Community

Although Burp Suite Community offers a more limited feature set compared to the Professional edition, it still provides an impressive array of tools that are highly valuable for web application testing. Let's explore some of the key features:

- **Proxy**: The Burp Proxy is the most renowned aspect of Burp Suite. It enables interception and modification of requests and responses while interacting with web applications.
- **Repeater**: Another well-known feature. [Repeater](https://tryhackme.com/room/burpsuiterepeater) allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error (e.g., in SQLi - Structured Query Language Injection) or testing the functionality of an endpoint for vulnerabilities.
- **Intruder**: Despite rate limitations in Burp Suite Community, [Intruder](https://tryhackme.com/room/burpsuiteintruder) allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.
- **Decoder**: [Decoder](https://tryhackme.com/room/burpsuiteom) offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target. While alternative services exist for this purpose, leveraging Decoder within Burp Suite can be highly efficient.
- **Comparer**: As the name suggests, [Comparer](https://tryhackme.com/room/burpsuiteom) enables the comparison of two pieces of data at either the word or byte level. While not exclusive to Burp Suite, the ability to send potentially large data segments directly to a comparison tool with a single keyboard shortcut significantly accelerates the process.
- **Sequencer**: [Sequencer](https://tryhackme.com/room/burpsuiteom) is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. If the algorithm used for generating these values lacks secure randomness, it can expose avenues for devastating attacks.

Beyond the built-in features, the Java codebase of Burp Suite facilitates the development of extensions to enhance the framework's functionality. These extensions can be written in Java, Python (using the Java Jython interpreter), or Ruby (using the Java JRuby interpreter). The **Burp Suite Extender** module allows for quick and easy loading of extensions into the framework, while the marketplace, known as the **BApp Store**, enables downloading of third-party modules. While certain extensions may require a professional license for integration, there are still a considerable number of extensions available for Burp Community. For instance, the **Logger++** module can extend the built-in logging functionality of Burp Suite.
<div>
<br>
<br>
</div>

### Questions

##### Which Burp Suite feature allows us to intercept requests between ourselves and the target?
Proxy

##### Which Burp tool would we use to brute-force a login form?
Intruder
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Installation

Burp Suite is one of those tools that is very useful to have around, whether for web or mobile application assessments, pentesting, bug bounty hunting, or even debugging features in web app development. Here's a guide on installing Burp Suite on different platforms:

**Note:** If you use the AttackBox, Burp Suite is already installed, so you can skip this step.
<div>
<br>
</div>

#### Downloads

To download the latest version of Burp Suite for other systems, you may click this [button](https://portswigger.net/burp/releases/) to go to their download page.

**Kali Linux:** Burp Suite comes pre-installed with Kali Linux. In case it is missing on your Kali installation, you can easily install it from the Kali apt repositories.

**Linux, macOS, and Windows:** For other operating systems, PortSwigger provides dedicated installers for Burp Suite Community and Burp Suite Professional on the Burp Suite downloads page. Choose your operating system from the dropdown menu and select **Burp Suite Community Edition**. Then, click the **Download** button to initiate the download.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/cf27fb99c50eb3c2784212d4f56a7b82.png)
<div>
<br>
</div>

#### Installation

Install Burp Suite using the appropriate method for your operating system. On Windows, run the executable file, while on Linux, execute the script from the terminal (with or without sudo). If you choose not to use `sudo` during installation on Linux, Burp Suite will be installed in your home directory at `~/BurpSuiteCommunity/BurpSuiteCommunity` and will not be added to your `PATH`.

The installation wizard provides clear instructions, and it is generally safe to accept the default settings. However, it is always recommended to review the installer carefully.

With Burp Suite successfully installed, you can now launch the application. In the next task, we will explore the initial setup and configuration.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. The Dashboard

You may use the pre-installed Burp Suite Community Edition in our AttackBox. To launch the AttackBox, click the **Start AttackBox** button at the top of this page.

Once you launch Burp Suite and accept the terms and conditions, you will be prompted to select a project type. In Burp Suite Community, the options are limited, and you can simply click **Next** to proceed.

The next window allows you to choose the configuration for Burp Suite. It is generally recommended to keep the default settings, which are suitable for most situations. Click **Start Burp** to open the main Burp Suite interface.

Upon opening Burp Suite for the first time, you might encounter a screen with training options. It is highly recommended to go through these training materials when you have the time.

If you don't see the training screen (or in subsequent sessions), you will be presented with the Burp Dashboard, which may seem overwhelming at first. However, it will soon become familiar.

The Burp Dashboard is divided into four quadrants, as labelled in counter-clockwise order starting from the top left:

![Showing the different quadrants in the dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/11202e4c73faa30a757f1439b63b85c6.png)

1. **Tasks**: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application. In Burp Suite Community, the default “Live Passive Crawl” task, which automatically logs the pages visited, is sufficient for our purposes in this module. Burp Suite Professional offers additional features like on-demand scans.

2. **Event log**: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

3. **Issue Activity**: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

4. **Advisory**: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. This information can be exported into a report. In Burp Suite Community, this section may not show any vulnerabilities.


Throughout the various tabs and windows of Burp Suite, you will notice question mark icons (![question mark icon](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/93d5f88c31c7e99d65fda7425a572406.png)).

Clicking on these icons opens a new window with helpful information specific to that section. These help icons are invaluable when you need assistance or clarification on a particular feature, so make sure to utilise them effectively.

![Help menu when the question mark logo is clicked](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/a68c56aa12934f1fa68758f086a0df3a.png)

By exploring the different tabs and functionalities of Burp Suite, you will gradually become familiar with its capabilities.
<div>
<br>
<br>
</div>

### Questions

##### What menu provides information about the actions performed by Burp Suite, such as starting the proxy, and details about connections made through Burp?
Event log
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Navigation

In Burp Suite, the default navigation is primarily done through the top menu bars, which allow you to switch between modules and access various sub-tabs within each module. The sub-tabs appear in a second menu bar directly below the main menu bar.

Here's how the navigation works:

1. **Module Selection**: The top row of the menu bar displays the available modules in Burp Suite. You can click on each module to switch between them. For example, the Burp Proxy module is selected in the image below.
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/cb50d9d010fd277b7ce2c9acf2481125.png)

2. **Sub-Tabs**: If a selected module has multiple sub-tabs, they can be accessed through the second menu bar that appears directly below the main menu bar. These sub-tabs often contain module-specific settings and options. For example, in the image above, the Proxy Intercept sub-tab is selected within the Burp Proxy module.

3. **Detaching Tabs**: If you prefer to view multiple tabs separately, you can detach them into separate windows. To do this, go to the **Window** option in the application menu above the **Module Selection** bar. From there, choose the "Detach" option, and the selected tab will open in a separate window. The detached tabs can be reattached using the same method.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/87c7b704d11abbed8e059a0d33672613.png)

Burp Suite also provides keyboard shortcuts for quick navigation to key tabs. By default, the following shortcuts are available:

|Shortcut|Tab|
|---|---|
|`Ctrl + Shift + D`|Dashboard|
|`Ctrl + Shift + T`|Target tab|
|`Ctrl + Shift + P`|Proxy tab|
|`Ctrl + Shift + I`|Intruder tab|
|`Ctrl + Shift + R`|Repeater tab|
<div>
<br>
<br>
</div>

### Questions

##### Which tab `Ctrl + Shift + P` will switch us to?
Proxy tab
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 7. Options

Before diving into the Burp Proxy, let's explore the available options for configuring Burp Suite. There are two types of settings: Global settings (also known as User settings) and Project settings.

- **Global Settings**: These settings affect the entire Burp Suite installation and are applied every time you start the application. They provide a baseline configuration for your Burp Suite environment.

- **Project Settings**: These settings are specific to the current project and apply only during the session. However, please note that Burp Suite Community Edition does not support saving projects, so any project-specific options will be lost when you close Burp.
	
	To access the settings, click on the **Settings** button in the top navigation bar. This will open a separate settings window.
    ![Settings button to open the separate settings window](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/40a3ea01d6eadc91d98499c3f921c90f.png)
    
    Below is the image showing the separate settings window.
    ![Separate settings window](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/8a6df0ac968a5c33e91903b350253b6b.png)

In the Settings window, you will find a menu on the left-hand side. This menu allows you to switch between different types of settings, including:

1. **Search**: Enables searching for specific settings using keywords.
2. **Type filter**: Filters the settings for **User** and **Project** options.
    - **User settings**: Shows settings that affect the entire Burp Suite installation.
    - **Project settings**: Displays settings specific to the current project.
3. **Categories**: Allows selecting settings by category.

![Project settings button](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/04cf1a4164616772d9495a3ee2bfd10a.png)  

It's worth noting that many tools within Burp Suite provide shortcuts to specific categories of settings. For example, the **Proxy** module includes a **Proxy settings** button that opens the settings window directly to the relevant proxy section.

![[Pasted image 20250913110133.png]]

The search feature on the settings page is a valuable addition, allowing you to quickly search for settings using keywords.

Take some time to familiarize yourself with the range of configurable options in Burp Suite. Once you are comfortable, you can proceed with the exercises related to configuring Burp Suite settings.
<div>
<br>
<br>
</div>

### Questions

##### In which category can you find a reference to a "Cookie jar"?
**Sessions**

##### In which base category can you find the "Updates" sub-category, which controls the Burp Suite update behavior?
**Sessions**

##### What is the name of the sub-category which allows you to change the keybindings for shortcuts in Burp Suite?
Hotkeys

##### If we have uploaded Client-Side TLS certificates, can we override these on a per-project basis (yea/nay)?
yea
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 8. Introduction to the Burp Proxy

The Burp Proxy is a fundamental and crucial tool within Burp Suite. It enables the capture of requests and responses between the user and the target web server. This intercepted traffic can be manipulated, sent to other tools for further processing, or explicitly allowed to continue to its destination.

#### Key Points to Understand About the Burp Proxy

- **Intercepting Requests:** When requests are made through the Burp Proxy, they are intercepted and held back from reaching the target server. The requests appear in the Proxy tab, allowing for further actions such as forwarding, dropping, editing, or sending them to other Burp modules. To disable the intercept and allow requests to pass through the proxy without interruption, click the `Intercept is on` button.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/73989984d0985412a3405ea1d6f8d171.png)

- **Taking Control:** The ability to intercept requests empowers testers to gain complete control over web traffic, making it invaluable for testing web applications.

- **Capture and Logging:** Burp Suite captures and logs requests made through the proxy by default, even when the interception is turned off. This logging functionality can be helpful for later analysis and review of prior requests.

- **WebSocket Support:** Burp Suite also captures and logs WebSocket communication, providing additional assistance when analysing web applications.

- **Logs and History:** The captured requests can be viewed in the **HTTP history** and **WebSockets history** sub-tabs, allowing for retrospective analysis and sending the requests to other Burp modules as needed.
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/8d5388b41dc847d2af38acf7ef4b116c.png)
    
    Proxy-specific options can be accessed by clicking the **Proxy settings** button. These options provide extensive control over the Proxy’s behavior and functionality. Familiarize yourself with these options to optimize your Burp Proxy usage.

#### Some Notable Features in the Proxy Settings

- **Response Interception:** By default, the proxy does not intercept server responses unless explicitly requested on a per-request basis. The "Intercept responses based on the following rules" checkbox, along with the defined rules, allows for a more flexible response interception.
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/e24fd91064186b78014d6afd773d60f3.png)
    
- **Match and Replace:** The "Match and Replace" section in the **Proxy settings** enables the use of regular expressions (regex) to modify incoming and outgoing requests. This feature allows for dynamic changes, such as modifying the user agent or manipulating cookies.

Take the time to explore and experiment with the Proxy options, as this will enhance your understanding and proficiency with the tool.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 9. Connecting through the Proxy (FoxyProxy)

Start the machine by clicking the **Start Machine** button below.

To use the Burp Suite Proxy, we need to configure our local web browser to redirect traffic through Burp Suite. In this task, we will focus on configuring the proxy using the FoxyProxy extension in Firefox.

Please note that the instructions provided are specific to Firefox. If you are using a different browser, you may need to find alternative methods or use the TryHackMe AttackBox.

Here are the steps to configure the Burp Suite Proxy with FoxyProxy:

1. **Install FoxyProxy:** Download and install the [FoxyProxy Basic extension](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/).
    **Note: FoxyProxy is already installed on the AttackBox.**

2. **Access FoxyProxy Options:** Once installed, a button will appear at the top right of the Firefox browser. Click on the FoxyProxy button to access the FoxyProxy options pop-up.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/fee3f150ebb4d9301023188fddc0458a.png)
    
2. **Create Burp Proxy Configuration:** In the FoxyProxy options pop-up, click the **Options** button. This will open a new browser tab with the FoxyProxy configurations. Click the **Add** button to create a new proxy configuration.
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/5a73425b5de3395c5db2962b9d613506.png)
    
3. **Add Proxy Details:** On the "Add Proxy" page, fill in the following values:
    
    - Title: `Burp` (or any preferred name)
    - Proxy IP: `127.0.0.1`
    - Port: `8080`
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/b2d6f2b724f123070ca434bf2759df91.png)
    
4. **Save Configuration:** Click **Save** to save the Burp Proxy configuration.
    
5. **Activate Proxy Configuration:** Click on the FoxyProxy icon at the top-right of the Firefox browser and select the `Burp` configuration. This will redirect your browser traffic through `127.0.0.1:8080`. Note that Burp Suite must be running for your browser to make requests when this configuration is activated.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/20f5e9db304d164b57c7f7d89fabc63a.png)
    
6. **Enable Proxy Intercept in Burp Suite:** Switch to Burp Suite and ensure that Intercept is turned on in the **Proxy** tab.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/9e0f6f47486737deff0e16c4e066120f.png)  
    
2. **Test the Proxy:** Open Firefox and try accessing a website, such as the homepage for `http://MACHINE_IP/`. Your browser will hang, and the proxy will populate with the HTTP request. Congratulations, you have successfully intercepted your first request!

**Remember the following:**

- When the proxy configuration is active, and the intercept is switched on in Burp Suite, your browser will hang whenever you make a request.
- Be cautious not to leave the intercept switched on unintentionally, as it can prevent your browser from making any requests.
- Right-clicking on a request in Burp Suite allows you to perform various actions, such as forwarding, dropping, sending to other tools, or selecting options from the right-click menu.

Take note of these details as you begin using the Burp Suite Proxy.

**Note:** Consider closing the other tabs in the AttackBox browser before enabling interception, as you will receive some WebSocket requests instead of request from the target VM.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 10. Site Map and Issue Definitions

The **Target** tab in Burp Suite provides more than just control over the scope of our testing. It consists of three sub-tabs:

1. **Site map**: This sub-tab allows us to map out the web applications we are targeting in a tree structure. Every page that we visit while the proxy is active will be displayed on the site map. This feature enables us to automatically generate a site map by simply browsing the web application. In Burp Suite Professional, we can also use the site map to perform automated crawling of the target, exploring links between pages and mapping out as much of the site as possible. Even with Burp Suite Community, we can still utilize the site map to accumulate data during our initial enumeration steps. It is particularly useful for mapping out APIs, as any API endpoints accessed by the web application will be captured in the site map.

2. **Issue definitions**: Although Burp Community does not include the full vulnerability scanning functionality available in Burp Suite Professional, we still have access to a list of all the vulnerabilities that the scanner looks for. The **Issue definitions** section provides an extensive list of web vulnerabilities, complete with descriptions and references. This resource can be valuable for referencing vulnerabilities in reports or assisting in describing a particular vulnerability that may have been identified during manual testing.

3. **Scope settings**: This setting allows us to control the target scope in Burp Suite. It enables us to include or exclude specific domains/IPs to define the scope of our testing. By managing the scope, we can focus on the web applications we are specifically targeting and avoid capturing unnecessary traffic.

Overall, the **Target** tab offers features beyond scoping, allowing us to map out web applications, fine-tune our target scope, and access a comprehensive list of web vulnerabilities for reference purposes.
<div>
<br>
</div>

#### Challenge

Take a look around the site on `http://10.10.42.160/` — we will be using this a lot throughout the module. Visit every other page that is linked on the homepage, then check your sitemap — one endpoint should stand out as being very unusual!

Visit this in your browser (or use the "Response" section of the site map entry for that endpoint)
<div>
<br>
<br>
</div>

### Questions

##### What is the flag you receive after visiting the unusual endpoint?
THM{NmNlZTliNGE1MWU1ZTQzMzgzNmFiNWVk}
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 11. The Burp Suite Browser
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 12. Scoping and Targeting
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 13. Proxying HTTPS
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 14. Example Attack
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 15. Conclusion
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/burpsuitebasics