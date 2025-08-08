# FRI 8TH AUG 2025
## Windows Defender Flagged My Obsidian Note as Malware – What Happened?

### Context

While writing notes in Obsidian (on SQL injection fundamentals from Hack The Box), my Markdown file was suddenly deleted without warning. I hadn't deleted it manually, so I investigated.
<div align="center">
<br>
<br>
</div>
### What I Found

Windows Security had flagged and **quarantined the note** as a threat:

- **Threat:** `Backdoor:PHP/Remoteshell.F`
- **Severity:** Severe
- **File Type:** `.md` (Markdown)
- **Action:** Quarantined (auto-deleted from my Obsidian vault)
- **Reason:** The note included a PHP code snippets resembling a backdoor payload, which triggered Windows Defender's malware detection.
<div align="center">
<br>
<br>
</div>

### Why It Happened

Windows Defender scans all files, including text files, for **code signatures** that match known malware. Educational notes that include **exploit code** or **webshells** (even in code blocks) can be misidentified as active threats.
<div align="center">
<br>
<br>
</div>

### ✅ **How to Prevent It (Safely)**

#### Option 1: Exclude Your Notes Folder from Windows Defender

- Go to **Windows Security > Virus & threat protection > Manage settings**
    
- Under **Exclusions**, add your Obsidian notes folder
    
- Only do this if you trust your files and are working in a controlled learning environment
    

#### Option 2: Fence Code Snippets Clearly

Use triple backticks with language tags:  
` markdown ```php <?php system($_GET['cmd']); ?> ``` `  
May not prevent detection, but keeps things structured.

#### Option 3: Store Exploit Code in Separate Files

- Save dangerous snippets in `.txt` or `.zip` files
    
- Store them in excluded folders or outside of synced vaults
    

---

### 🔐 **Bonus Tip: Re-enable PUA Protection**

If Defender warns that _"Settings to block potentially unwanted apps are turned off"_:

- Go to **Windows Security > App & browser control > Reputation-based protection**
    
- Turn **PUA Protection** back on
    

---

### 🧪 Takeaway

Even notes can trigger antivirus if they contain exploit code. This is a great example of:

- How antivirus software works
    
- Why cybersecurity environments need proper exclusions
    
- The importance of controlled, secure learning setups
    

---

Let me know if you want this as a downloadable file too (Markdown, PDF, etc.) — happy to help!