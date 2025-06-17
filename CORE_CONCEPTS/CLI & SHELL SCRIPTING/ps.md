
The `ps` command is:
- ✅ **A standard command in Bash (and other Unix/Linux shells)** — it stands for **"process status"**, and it’s used to display information about running processes.
- ✅ **Also available in PowerShell**, but it **behaves differently**.

### In **Bash (Linux/macOS)**:

```bash
ps aux
```

This lists all running processes with detailed info.


### 📌 In **PowerShell (Windows)**:

```powershell
ps
```

This is actually an **alias** for:

```powershell
Get-Process
```

So:

```powershell
ps
```

Will show a list of running processes, similar to Task Manager. But the output format and options are different from Bash's `ps`.

---

### ✅ Summary:

|Environment|Command|Purpose|
|---|---|---|
|Bash|`ps`|Show process list (native)|
|PowerShell|`ps`|Alias for `Get-Process`|

So yes, `ps` can be used in **both Bash and PowerShell**, but it **means different things** in each context.