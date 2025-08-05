## Introduction

Welcome to the `Attacking Web Applications with Ffuf` module!

There are many tools and methods to utilize for directory and parameter fuzzing/brute-forcing. In this module we will mainly focus on the [ffuf](https://github.com/ffuf/ffuf) tool for web fuzzing, as it is one of the most common and reliable tools available for web fuzzing.

The following topics will be discussed:

- Fuzzing for directories
- Fuzzing for files and extensions
- Identifying hidden vhosts
- Fuzzing for PHP parameters
- Fuzzing for parameter values

Tools like `ffuf` help us automatically test parts of a website to see what exists. For example, we can give it a list of possible page names, and it will try each one by sending a request to the website. If the website responds with a code 200 (which means "OK"), that tells us the page exists, and we can then check it out ourselves.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Web Fuzzing

We will start by learning the basics of using `ffuf` to fuzz websites for directories. We run the exercise in the question below, and visit the URL it gives us, and we see the following website:

![[Pasted image 20250804191939.png]]

The website has no links to anything else, nor does it give us any information that can lead us to more pages. So, it looks like our only option is to '`fuzz`' the website.
<div align="center">
<br>
<br>
</div>

### Fuzzing

==The term DEF-fuzzing refers to a testing technique that sends various types of user input to a certain interface to study how it would react==. If we were fuzzing for SQL injection vulnerabilities, we would be sending random special characters and seeing how the server would react. If we were fuzzing for a buffer overflow, we would be sending long strings and incrementing their length to see if and when the binary would break.

We usually utilize pre-defined wordlists of commonly used terms for each type of test for web fuzzing to see if the webserver would accept them. This is done because web servers do not usually provide a directory of all available links and domains (unless terribly configured), and so we would have to check for various links and see which ones return pages. For example, if we visit [https://www.hackthebox.eu/doesnotexist](https://www.hackthebox.eu/doesnotexist), we would get an HTTP code `404 Page Not Found`, and see the below page:

![404 error page with 'Are you lost?' message and 'Back to Home' button.](https://academy.hackthebox.com/storage/modules/54/web_fnb_HTB_404.jpg)

However, if we visit a page that exists, like `/login`, we would get the login page and get an HTTP code `200 OK`, and see the below page:
 
![Hack The Box logo with 'Login' text on dark background.](https://academy.hackthebox.com/storage/modules/54/web_fnb_HTB_login.jpg)

This is the basic idea behind web fuzzing for pages and directories. Still, we cannot do this manually, as it will take forever. This is why we have tools that do this automatically, efficiently, and very quickly. Such tools send hundreds of requests every second, study the response HTTP code, and determine whether the page exists or not. Thus, we can quickly determine what pages exist and then manually examine them to see their content.
<div align="center">
<br>
<br>
</div>

### Wordlists

To determine which pages exist, we should have a wordlist containing commonly used words for web directories and pages, very similar to a `Password Dictionary Attack`, which we will discuss later in the module. Though this will not reveal all pages under a specific website, as some pages are randomly named or use unique names, in general, this returns the majority of pages, reaching up to 90% success rate on some websites.

We will not have to reinvent the wheel by manually creating these wordlists, as great efforts have been made to search the web and determine the most commonly used words for each type of fuzzing. Some of the most commonly used wordlists can be found under the GitHub [SecLists](https://github.com/danielmiessler/SecLists) repository, which categorizes wordlists under various types of fuzzing, even including commonly used passwords, which we'll later utilize for Password Brute Forcing.

Within our PwnBox, we can find the entire `SecLists` repo available under `/opt/useful/SecLists`. The specific wordlist we will be utilizing for pages and directory fuzzing is another commonly used wordlist called `directory-list-2.3`, and it is available in various forms and sizes. We can find the one we will be using under:

```shell-session
codenvibes@htb[/htb]$ locate directory-list-2.3-small.txt

/opt/useful/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
```

Tip: Taking a look at this wordlist we will notice that it contains copyright comments at the beginning, which can be considered as part of the wordlist and clutter the results. We can use the following in `ffuf` to get rid of these lines with the `-ic` flag.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Directory Fuzzing

Now that we understand the concept of Web Fuzzing and know our wordlist, we should be ready to start using `ffuf` to find website directories.
<div align="center">
<br>
<br>
</div>


## Ffuf

`Ffuf` is pre-installed on your PwnBox instance. If you want to use it on your own machine, you can either use "`apt install ffuf -y`" or download it and use it from its [GitHub Repo](https://github.com/ffuf/ffuf.git). As a new user of this tool, we will start by issuing the `ffuf -h` command to see how the tools can be used:

```shell-session
codenvibes@htb[/htb]$ ffuf -h

HTTP OPTIONS:
  -H               Header `"Name: Value"`, separated by colon. Multiple -H flags are accepted.
  -X               HTTP method to use (default: GET)
  -b               Cookie data `"NAME1=VALUE1; NAME2=VALUE2"` for copy as curl functionality.
  -d               POST data
  -recursion       Scan recursively. Only FUZZ keyword is supported, and URL (-u) has to end in it. (default: false)
  -recursion-depth Maximum recursion depth. (default: 0)
  -u               Target URL
...SNIP...

MATCHER OPTIONS:
  -mc              Match HTTP status codes, or "all" for everything. (default: 200,204,301,302,307,401,403)
  -ms              Match HTTP response size
...SNIP...

FILTER OPTIONS:
  -fc              Filter HTTP status codes from response. Comma separated list of codes and ranges
  -fs              Filter HTTP response size. Comma separated list of sizes and ranges
...SNIP...

INPUT OPTIONS:
...SNIP...
  -w               Wordlist file path and (optional) keyword separated by colon. eg. '/path/to/wordlist:KEYWORD'

OUTPUT OPTIONS:
  -o               Write output to file
...SNIP...

EXAMPLE USAGE:
  Fuzz file paths from wordlist.txt, match all responses but filter out those with content-size 42.
  Colored, verbose output.
    ffuf -w wordlist.txt -u https://example.org/FUZZ -mc all -fs 42 -c -v
...SNIP...
```

As we can see, the `help` output is quite large, so we only kept the options that may become relevant for us in this module.
<div align="center">
<br>
<br>
</div>

## Directory Fuzzing

As we can see from the example above, the main two options are `-w` for wordlists and `-u` for the URL. We can assign a wordlist to a keyword to refer to it where we want to fuzz. For example, we can pick our wordlist and assign the keyword `FUZZ` to it by adding `:FUZZ` after it:

```shell-session
codenvibes@htb[/htb]$ ffuf -w /opt/useful/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ
```
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

#### First: What is `ffuf` trying to do?

Imagine you're trying to find **hidden folders** on a website like:

```
http://example.com/admin
http://example.com/images
http://example.com/backup
```

You don’t know these folder names ahead of time. So you give `ffuf` a **wordlist** — a list of guesses — and tell it:

> “Hey ffuf, try each of these words in the URL and tell me which ones work.”
<div align="center">
<br>
<br>
</div>

#### So where do keywords come in?

To make that work, `ffuf` needs:

1. ==The **list of words to try**==
2. ==The **place in the request to put those words**==

That’s what `-w` and `FUZZ` are for:
<div align="center">
<br>
<br>
</div>

#### Breaking down the command

```bash
ffuf -w wordlist.txt:FUZZ -u http://example.com/FUZZ
```

##### `-w wordlist.txt:FUZZ`

This tells `ffuf`:

> “Use this file (`wordlist.txt`) as the source of words. I’m calling this list `FUZZ`.”

If your wordlist looks like this:

```
admin
images
backup
```

Then `FUZZ` now means:  
👉 Try "admin", then "images", then "backup".
<div align="center">
<br>
<br>
</div>

##### `-u http://example.com/FUZZ`

This tells `ffuf`:

> “Put each word from `FUZZ` **right here in the URL**.”

So ffuf makes requests like:

```
http://example.com/admin
http://example.com/images
http://example.com/backup
```

It checks if those pages exist. If one does, you’ve found a hidden folder.
<div align="center">
<br>
<br>
</div>

#### Why is the path being "assigned"?

You’re **assigning a wordlist to a keyword** (`FUZZ`) so that `ffuf` knows:

- What words to try (`-w ...`)
- Where to try them (`-u ...FUZZ...`)
<div align="center">
<br>
<br>
</div>

#### Example without the keyword (FUZZ is the default)

This is also valid:

```bash
ffuf -w wordlist.txt -u http://example.com/FUZZ
```

Because if you don’t name the keyword (`:FUZZ`), ffuf assumes it's called `FUZZ`.

==But once you want to use **multiple wordlists in different parts** (like for file extensions or parameters), you'll need to name them:==

```bash
-w dirs.txt:DIR -w extensions.txt:EXT -u http://example.com/DIR.EXT
```##


Next, as we want to be fuzzing for web directories, we can place the `FUZZ` keyword where the directory would be within our URL, with:

```shell-session
codenvibes@htb[/htb]$ ffuf -w <SNIP> -u http://SERVER_IP:PORT/FUZZ
```
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
<br>
</div>

Now, let's start our target in the question below and run our final command on it:

```shell-session
codenvibes@htb[/htb]$ ffuf -w /opt/useful/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ


        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.1.0-git
________________________________________________

 :: Method           : GET
 :: URL              : http://SERVER_IP:PORT/FUZZ
 :: Wordlist         : FUZZ: /opt/useful/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403
________________________________________________

<SNIP>
blog                    [Status: 301, Size: 326, Words: 20, Lines: 10]
:: Progress: [87651/87651] :: Job [1/1] :: 9739 req/sec :: Duration: [0:00:09] :: Errors: 0 ::
```

We see that `ffuf` tested for almost 90k URLs in less than 10 seconds. This speed may vary depending on your internet speed and ping if you used `ffuf` on your machine, but it should still be extremely fast.

We can even make it go faster if we are in a hurry by increasing the number of threads to 200, for example, with `-t 200`, but this is not recommended, especially when used on a remote site, as it may disrupt it, and cause a `Denial of Service`, or bring down your internet connection in severe cases. We do get a couple of hits, and we can visit one of them to verify that it exists:

![[Pasted image 20250805060116.png]]

We get an empty page, indicating that the directory does not have a dedicated page, but also shows that we do have access to it, as we do not get an HTTP code `404 Not Found` or `403 Access Denied`. In the next section, we will look for pages under this directory to see whether it is really empty or has hidden files and pages.
<div align="center">
<br>
<br>
</div>

### Questions

##### In addition to the directory we found above, there is another directory that can be found. What is it?
forum

```shell
┌──(mopsy㉿APHP)-[~/HTB]
└─$ ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://94.237.50.221:46733/FUZZ

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v2.1.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://94.237.50.221:46733/FUZZ
 :: Wordlist         : FUZZ: /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
________________________________________________

#                       [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 150ms]
forum                   [Status: 301, Size: 323, Words: 20, Lines: 10, Duration: 142ms]
# Priority-ordered case-sensitive list, where entries were found [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 1070ms]
# on at least 3 different hosts [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 2078ms]
# or send a letter to Creative Commons, 171 Second Street, [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 3060ms]
# Copyright 2007 James Fisher [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 3123ms]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 4060ms]
# Attribution-Share Alike 3.0 License. To view a copy of this [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 4062ms]
# directory-list-2.3-small.txt [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 4067ms]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 5070ms]
# license, visit http://creativecommons.org/licenses/by-sa/3.0/ [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 5069ms]
# Suite 300, San Francisco, California, 94105, USA. [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 5068ms]
blog                    [Status: 301, Size: 322, Words: 20, Lines: 10, Duration: 5074ms]
                        [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 5074ms]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 5075ms]
# This work is licensed under the Creative Commons [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 6081ms]
                        [Status: 200, Size: 986, Words: 423, Lines: 56, Duration: 143ms]
:: Progress: [87664/87664] :: Job [1/1] :: 274 req/sec :: Duration: [0:05:39] :: Errors: 0 ::

```

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Page Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Recursive Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## DNS Records
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Sub-domain Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Vhost Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Filtering Results
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Parameter Fuzzing - GET
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Parameter Fuzzing - POST
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Value Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Skills Assessment - Web Fuzzing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>


---

## References

https://academy.hackthebox.com/module/details/54