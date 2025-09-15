#THMLP-JR_PENETRATION_TESTER #THMMOD-BURP_SUITE #Burp_Suite

## 1. Introduction

#### Welcome to the Burp Suite Other Modules room!

In addition to the widely recognized [Repeater](https://tryhackme.com/room/burpsuiterepeater) and [Intruder](https://tryhackme.com/room/burpsuiteintruder) rooms, Burp Suite incorporates several lesser-known modules. These will form the focus of this room's exploration.

The spotlight will be on the Decoder, Comparer, Sequencer, and Organizer tools. They facilitate operations with encoded text, enable comparison of data sets, allow the analysis of randomness within captured tokens, and help you store and annotate copies of HTTP messages that you may want to revisit later. Although these tasks appear straightforward, accomplishing them within Burp Suite can substantially save time, thus emphasizing the importance of learning to use these modules effectively.

Without further ado, let's delve into the first tool, the Decoder.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Decoder: Overview

The Decoder module of Burp Suite gives user data manipulation capabilities. As implied by its name, it not only decodes data intercepted during an attack but also provides the function to encode our own data, prepping it for transmission to the target. Decoder also allows us to create hashsums of data, as well as providing a Smart Decode feature, which attempts to decode provided data recursively until it is back to being plaintext (like the "Magic" function of [Cyberchef](https://gchq.github.io/CyberChef/)).

To access the Decoder, navigate to the Decoder tab from the top menu to view the available options:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/2258ccd03e0732c2d0bd4729a3f6212f.png)

This interface lays out a multitude of options.

1. This box serves as the workspace for entering or pasting data that requires encoding or decoding. Consistent with other modules of Burp Suite, data can be moved to this area from different parts of the framework via the **Send to Decoder** option upon right-clicking.
2. At the top of the list on the right, there's an option to treat the input as either text or hexadecimal byte values.
3. As we move down the list, dropdown menus are present to encode, decode, or hash the input.
4. The **Smart Decode** feature, located at the end, attempts to auto-decode the input.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/f795b0f0701d019d37025310fa4ae285.png)

Upon entering data into the input field, the interface replicates itself to present the output of our operation. We can then choose to apply further transformations using the same options:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/257ef62054a79fe68172310bfcb4c002.png)
<div>
<br>
<br>
</div>

### Questions

##### Which feature attempts auto-decode of the input?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Decoder: Encoding/Decoding

#### Encoding and Decoding with Decoder

Now, let's examine the manual encoding and decoding options in detail. These are identical whether the decoding or encoding menu is chosen:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/8ce7c550edf3a79cafbb7be8468793ff.png)

- **Plain**: This refers to the raw text before any transformations are applied.

- **URL**: URL encoding is utilized to ensure the safe transfer of data in the URL of a web request. It involves substituting characters for their ASCII character code in hexadecimal format, preceded by a percentage symbol (%). This method is vital for any type of web application testing.
    
    For instance, encoding the forward-slash character (**/**), whose ASCII character code is 47, converts it to **2F** in hexadecimal, thus becoming **%2F** in URL encoding. The Decoder can be used to verify this by typing a forward slash in the input box, then selecting`Encode as -> URL` :
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/72ecaaf06fc248457d61c079d6d98e8f.png)
    
- **HTML**: HTML Entities encoding replaces special characters with an ampersand (&), followed by either a hexadecimal number or a reference to the character being escaped, and ending with a semicolon (;). This method ensures the safe rendering of special characters in HTML and helps prevent attacks such as XSS. The HTML option in Decoder allows any character to be encoded into its HTML escaped format or decode captured HTML entities. For instance, to decode a previously discussed quotation mark, input the encoded version and choose `Decode as -> HTML`:
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/99ccb4aba6cb243b7c3b990e82061a86.png)
    
- **Base64**: Base64, a commonly used encoding method, converts any data into an ASCII-compatible format. The under-the-hood functioning isn't crucial at this stage; however, interested individuals can find the underlying mathematics [here](https://stackabuse.com/encoding-and-decoding-base64-strings-in-python).

- **ASCII Hex**: This option transitions data between ASCII and hexadecimal representations. For instance, the word "ASCII" can be converted into the hexadecimal number "4153434949". Each character is converted from its numeric ASCII representation into hexadecimal.

- **Hex, Octal, and Binary**: These encoding methods apply solely to numeric inputs, converting between decimal, hexadecimal, octal (base eight), and binary representations.

- **Gzip**: Gzip compresses data, reducing file and page sizes before browser transmission. Faster load times are highly desirable for developers looking to enhance their SEO score and avoid user inconvenience. Decoder facilitates the manual encoding and decoding of gzip data, although it often isn't valid ASCII/Unicode. For instance:
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/01db98e37c59a26e307eb29cd9e04139.png)
    
These methods can be stacked. For example, a phrase ("Burp Suite Decoder") could be converted to ASCII Hex and then to octal:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/4a1065502dd1020858694994767b4156.gif)

In combination, these methods grant us substantial control over the data we are encoding or decoding.

Each encoding/decoding method is color-coded, enabling swift identification of the applied transformation.
<div>
<br>
</div>

##### Hex Format

While inputting data in ASCII format is beneficial, there are times when byte-by-byte input editing is necessary. This is where "Hex View" proves useful, selectable above the decoding options:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/704444afc761deabd6a8a3492dffd89b.png)

This feature enables us to view and alter our data in hexadecimal byte format, a vital tool when working with binary files or other non-ASCII data.
<div>
<br>
</div>

##### Smart Decode

Lastly, we have the **Smart decode** option. This feature tries to auto-decode encoded text. For instance, `&#x42;&#x75;&#x72;&#x70;&#x20;&#x53;&#x75;&#x69;&#x74;&#x65;` is automatically recognized as HTML encoded and is accordingly decoded:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d9e176315f8850e719252ed/room-content/e6330851dfa9ea47e3d2d54ab78b0023.gif)

While not perfect, this feature can be a quick solution for decoding unknown data chunks.
<div>
<br>
<br>
</div>

### Questions

##### Base64 encode the phrase: `Let's Start Simple`.<br><br>What is the base64 encoded version of this text?
##### URL Decode this data: `%4e%65%78%74%3a%20%44%65%63%6f%64%69%6e%67`.<br><br>What is the plaintext returned?
##### Use Smart decode to decode this data: `&#x25;&#x33;&#x34;&#x25;&#x33;&#x37;`.<br><br>What is the decoded text?
##### Encode this phrase: `Encoding Challenge`.<br><br>Start with base64 encoding. Take the output of this and convert it into ASCII Hex. Finally, encode the hex string into octal_._<br><br>What is the final string?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. Decoder: Hashing

`Hash`In addition to its Encoding/Decoding functionality, Decoder also offers the ability to generate hashsums for our data.
<div>
<br>
</div>

#### Theory

Hashing is a one-way process that transforms data into a unique signature. For a function to qualify as a hashing algorithm, the output it generates must be irreversible. A proficient hashing algorithm ensures that every data input will generate a completely unique hash. For instance, using the MD5 algorithm to produce a hashsum for the text "MD5sum" returns `4ae1a02de5bd02a5515f583f4fca5e8c`. Using the same algorithm for "MD5SUM" yields an entirely different hash despite the close resemblance of the input: `13b436b09172400c9eb2f69fbd20adad`. Therefore, hashes are commonly used to verify the integrity of files and documents, as even a tiny alteration to the file significantly changes the hashsum.

**Note:** The MD5 algorithm is deprecated and should not be used for contemporary applications.

Moreover, hashes are used to securely store passwords since the one-way hashing process makes the passwords relatively secure, even if the database is compromised. When a user creates a password, the application hashes and stores it. During login, the application hashes the submitted password and compares it against the stored hash; if they match, the password is correct. Using this method, an application never needs to store the original (plaintext) password.
<div>
<br>
</div>

#### Hashing in Decoder

Decoder allows us to create hashsums for data directly within Burp Suite; it operates similarly to the encoding/decoding options we discussed earlier. Specifically, we click on the **Hash** dropdown menu and select an algorithm from the list:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/c212c8a83418b3674928270f258ddd72.png)

**Note:** This list is significantly longer than the encoding/decoding algorithms – it's worth scrolling through to see the many available hashing algorithms.

Continuing with our earlier example, let's enter "MD5sum" into the input box, then scroll down the list until we find "MD5". Applying this automatically takes us into the Hex view:
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/01a73d9cb47f274259543585f91a3664.png" alt=""></div>

A hashing algorithm's output does not yield pure ASCII/Unicode text. Hence, it's customary to convert the algorithm's output into a hexadecimal string; this is the "hash" form you might be familiar with.

Let's complete this by applying an "ASCII Hex" encoding to the hashsum to create the neat hex string from our initial example.

Here's the full process:
<div align="center"><br><img width="" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/8bb114a4bce68b068f6dd0c0aaffe9e1.gif" alt=""></div>
<div>
<br>
<br>
</div>

### Questions

##### Using Decoder, what is the SHA-256 hashsum of the phrase: `Let's get Hashing!`?<br>Convert this into an ASCII Hex string for the answer to this question.
##### Generate an MD4 hashsum of the phrase: `Insecure Algorithms`.<br>Encode this as base64 (not ASCII Hex) before submitting.
##### Let's look at an in-context example:<br>First, download the file attached to this task.<br>**Note:** This file can also be downloaded from the deployed VM with `wget http://MACHINE_IP:9999/AlteredKeys.zip` — you may find this helpful if you are using the AttackBox.<br>Now read the problem specification below:  <br>"Some joker has messed with my SSH key! There are four keys in the directory, and I have no idea which is the real one. The MD5 hashsum for my key is `3166226048d6ad776370dc105d40d9f8` — could you find it for me?"<br>What is the correct key name?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Comparer: Overview
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Comparer: Example
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 7. Sequencer: Overview
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 8. Sequencer: Live Capture
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 9. Sequencer: Analysis
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 10. Organizer: Overview
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 11. Conclusion
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/burpsuiteom