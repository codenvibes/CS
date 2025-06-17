#bash #powershell 

The `ps` command is:
- ✅ **A standard command in Bash (and other Unix/Linux shells)** — it stands for **"process status"**, and it’s used to display information about running processes.
- ✅ **Also available in PowerShell**, but it **behaves differently**.

Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order In which the process starts. I.e. the 60th process will have a PID of 60.

### In Bash (Linux/macOS):

```bash
ps aux
```

This lists all running processes with detailed info.


### In PowerShell (Windows):

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


### Summary:

|Environment|Command|Purpose|
|---|---|---|
|Bash|`ps`|Show process list (native)|
|PowerShell|`ps`|Alias for `Get-Process`|


---

# References

https://tryhackme.com/room/linuxfundamentalspart3