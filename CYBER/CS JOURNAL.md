# FRI 8TH AUG 2025
## Windows Defender Flagged My Obsidian Note as Malware – What Happened?

### Context

While writing notes in Obsidian (on SQL injection fundamentals from Hack The Box), my Markdown file was suddenly deleted without warning. I hadn't deleted it manually, so I investigated.
<div align="center">
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
</div>

### Why It Happened

Windows Defender scans all files, including text files, for **code signatures** that match known malware. Educational notes that include **exploit code** or **webshells** (even in code blocks) can be misidentified as active threats.
<div align="center">
<br>
</div>

### How I Prevent It (Safely)<br>I Excluded my Obsidian Vault from Windows Defender

- Go to **Windows Security > Virus & threat protection > Manage settings**
- Under **Exclusions**, add your Obsidian notes folder
- Only do this if you trust your files and are working in a controlled learning environment
<div align="center">
<br>
</div>

### Takeaway

Even notes can trigger antivirus if they contain exploit code. This is a great example of:
- How antivirus software works
- Why cybersecurity environments need proper exclusions
- The importance of controlled, secure learning setups

---
