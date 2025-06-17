#bash #powershell 

The `ps` command is:
- ✅ **A standard command in Bash (and other Unix/Linux shells)** — it stands for **"process status"**, and it’s used to display information about running processes.
- ✅ **Also available in PowerShell**, but it **behaves differently**.

Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order In which the process starts. I.e. the 60th process will have a PID of 60.

### In Bash (Linux/macOS):
#### `ps`

By default, this shows **only processes running in the current shell/session** (your terminal) **that you own**.

Example:

```bash
ps
```

Output (only a few lines):

```
  PID TTY          TIME CMD
12345 pts/0    00:00:00 bash
12356 pts/0    00:00:00 ps
```

Only shows:
- The shell
- The `ps` command itself (since you're running it)


#### `ps aux`

This is the **standard way to list _all_ processes on the system** — across all users, not just yours.

##### Breakdown:

- `a` – show processes from **all users**
- `u` – show the user/owner of the process
- `x` – show processes **not attached to a terminal** (like daemons, background services)

Example:

```bash
ps aux
```

Output (much more detailed):

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  22556  1044 ?        Ss   09:00   0:01 /sbin/init
user      1234  0.0  0.2  54320  2024 ?        Sl   09:01   0:03 /usr/bin/gnome-shell
user      5678  0.0  0.0   4268   832 pts/0    R+   10:00   0:00 ps aux
```

#### Summary:

| Command  | Shows                                         | Use When You Want To...                         |
| -------- | --------------------------------------------- | ----------------------------------------------- |
| `ps`     | Your own shell-related processes              | Quickly see what’s running _in your terminal_   |
| `ps aux` | **All** processes for **all** users, detailed | Monitor the whole system or troubleshoot issues |

Let me know if you want to filter by name, PID, memory usage, etc. — that's easy too!


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