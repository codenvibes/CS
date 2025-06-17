#bash 

The `top` command is a **real-time system monitoring tool** available on **Unix-like systems** (such as Linux and macOS). It displays live information about system processes, including:
- CPU usage
- Memory usage
- Running tasks
- Process IDs (PIDs)
- User running each process
- Time each process has been running


## Example Output (Linux):

```bash
top
```

```
┌──(mopsy㉿APHP)-[~]
└─$ top
top - 08:23:17 up 48 min,  0 user,  load average: 0.36, 0.49, 0.43
Tasks:  14 total,   1 running,  13 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 99.1 id,  0.9 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3862.9 total,   2955.7 free,    667.2 used,    469.2 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3195.6 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    431 mopsy     20   0   10344   5044   2948 R   0.7   0.1   0:01.92 top
      1 root      20   0   22700  13640  10512 S   0.0   0.3   0:03.85 systemd
      2 root      20   0    2784   1928   1796 S   0.0   0.0   0:00.20 init-systemd(ka
      6 root      20   0    2776      4      0 S   0.0   0.0   0:00.00 init
    125 root      20   0    2792    212     80 S   0.0   0.0   0:00.00 SessionLeader
    126 root      20   0    2792    216     80 S   0.0   0.0   0:00.12 Relay(127)
    127 mopsy     20   0    7416   4228   3528 S   0.0   0.1   0:00.08 bash
    128 root      20   0    7220   3620   3100 S   0.0   0.1   0:00.03 login
    135 mopsy     20   0    4332   3728   3152 S   0.0   0.1   0:00.02 bash
    167 root      20   0   33760  12088  11040 S   0.0   0.3   0:00.87 systemd-journal
    179 root      20   0   31320   9412   7672 S   0.0   0.2   0:01.60 systemd-udevd
    238 root      20   0    4268   2588   2336 S   0.0   0.1   0:00.16 cron
    239 message+  20   0    6780   3668   3344 S   0.0   0.1   0:00.34 dbus-daemon
    245 root      20   0   17648   6904   5972 S   0.0   0.2   0:00.50 systemd
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