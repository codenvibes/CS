
The `top` command is a **real-time system monitoring tool** available on **Unix-like systems** (such as Linux and macOS). It displays live information about system processes, including:

- CPU usage
- Memory usage
- Running tasks
- Process IDs (PIDs)
- User running each process
- Time each process has been running

---

### 🔧 Example Output (Linux):

```bash
top
```

```
top - 10:31:01 up  1:42,  2 users,  load average: 0.50, 0.45, 0.25
Tasks: 160 total,   2 running, 158 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.0 us,  1.0 sy,  0.0 ni, 93.5 id,  0.5 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8054352 total,  1219832 free,  3245000 used,  3589520 buff/cache
PID  USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
2020 user      20   0  267848   8240   6984 S   1.3  0.1   0:00.39 gnome-terminal-
```

---

### ✅ Is `top` available in:

|Shell / OS|`top` Available?|Alternative|
|---|---|---|
|**Bash (Linux/macOS)**|✅ Yes|`htop` (more user-friendly)|
|**PowerShell (Windows)**|❌ No (Not natively)|`Get-Process`, `tasklist`, or use `top` via WSL|

---

### 🔄 Alternatives in PowerShell / Windows:

1. **Get-Process** (PowerShell)
    
    ```powershell
    Get-Process | Sort-Object CPU -Descending | Select-Object -First 10
    ```
    
2. **Tasklist** (CMD and PowerShell)
    
    ```cmd
    tasklist
    ```
    
3. **Windows Task Manager** (GUI)
    
4. **WSL** (Windows Subsystem for Linux)  
    If you're using WSL, you can run `top` exactly as on Linux:
    
    ```bash
    top
    ```
    

---

### Summary:

- `top` is a Linux/macOS command for real-time system monitoring.
    
- **Available in Bash**, not **natively in PowerShell**.
    
- Use `Get-Process` or install WSL if you want to use `top` on Windows.

---

## References