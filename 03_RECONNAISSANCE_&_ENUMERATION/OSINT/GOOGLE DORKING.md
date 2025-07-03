**Google Dorking** (also called **Google Hacking**) is the practice of using advanced Google search operators to find information that is not easily accessible through normal search queries.
You can, for instance, pick out results from a certain domain name using the **site:** filter, for example (site:[tryhackme.com](http://tryhackme.com/)) you can then match this up with certain search terms, say, for example, the word admin (site:tryhackme.com admin) this then would only return results from the [tryhackme.com](http://tryhackme.com/) website which contain the word admin in its content. You can combine multiple filters as well. Here is an example of more filters you can use:

| **Filter** | **Example**        | **Description**                                              |
| ---------- | ------------------ | ------------------------------------------------------------ |
| site       | site:tryhackme.com | returns results only from the specified website address      |
| inurl      | inurl:admin        | returns results that have the specified word in the URL      |
| filetype   | filetype:pdf       | returns results which are a particular file extension        |
| intitle    | intitle:admin      | returns results that contain the specified word in the title |


| Operator             | Use                                                                       | Example              |
| -------------------- | ------------------------------------------------------------------------- | -------------------- |
| `site:`              | Limit search to a domain                                                  | `site:example.com`   |
| `filetype:` / `ext:` | Find specific file types                                                  | `filetype:pdf`       |
| `intitle:`           | Keywords in page title                                                    | `intitle:"index of"` |
| `inurl:`             | Keywords in URL (returns results that have the specified word in the URL) | `inurl:admin`        |
| `allintext:`         | Keywords in page body                                                     | `allintext:password` |
| `cache:`             | Google’s cached version                                                   | `cache:example.com`  |
| `OR`                 | Combine terms                                                             | `"login" OR "admin"` |

## Google Dorking & Search Operators — Quick Reference

### Official Google Search Operator Resources

- **Google Advanced Search Page:**  
    [https://www.google.com/advanced_search](https://www.google.com/advanced_search)
 
- **Google Search Help — Refine Web Searches:**  
    [https://support.google.com/websearch/answer/2466433?hl=en](https://support.google.com/websearch/answer/2466433?hl=en)
   

### Comprehensive Google Dork Database

- **Exploit-DB Google Hacking Database (GHDB):**  
    [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)


### Community Cheat Sheets & Collections

- **GitHub:** Search _“Google Dork Cheat Sheet GitHub”_ for user-maintained lists.  
    Example:  
    [https://github.com](https://github.com/) → search for **Google Dork Cheat Sheet**.

- **HackTricks (by Carlos Polop):** Practical OSINT & Dorking tricks.  
    [https://book.hacktricks.xyz](https://book.hacktricks.xyz/)

- **Offensive Security:** Resources often mention advanced dorking for pentesting.


---

## References

https://tryhackme.com/room/contentdiscovery