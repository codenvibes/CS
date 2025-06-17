#bash 

The `kill` command is used to **send signals to processes**, most commonly to **terminate (kill) a process** by its PID (Process ID).


### Basic Syntax:

```bash
kill [options] <PID>
```

By default, `kill` sends the `SIGTERM` (signal 15) — a polite request to terminate the process.


### Common Use in Bash/Linux/macOS:

```bash
kill 1234           # Sends SIGTERM to process with PID 1234
kill -9 1234        # Sends SIGKILL (force kill) to PID 1234
kill -15 1234       # Explicitly sends SIGTERM
```

### Signals:

| Signal    | Number | Meaning                                  |
| --------- | ------ | ---------------------------------------- |
| `SIGTERM` | 15     | Graceful termination (default)           |
| `SIGKILL` | 9      | Forceful termination (cannot be ignored) |
| `SIGHUP`  | 1      | Hang up / restart                        |
| `SIGSTOP` | 19     | Pause process                            |

To list all available signals:

```bash
kill -l
```


### How to find a PID:

```bash
ps aux | grep process_name
top            # or use htop
```

---

## ❌ `kill` in **PowerShell/Windows**:

PowerShell does **not** have a native `kill` command, but you can terminate processes with:

#### 1. `Stop-Process` (PowerShell equivalent):

```powershell
Stop-Process -Id 1234
Stop-Process -Name "notepad"
```

#### 2. `taskkill` (CMD or PowerShell):

```cmd
taskkill /PID 1234 /F     # Forcefully ends process by PID
taskkill /IM notepad.exe /F
```

---

### Summary:

|Shell|Kill Command|Example|
|---|---|---|
|Bash/Linux|`kill`, `kill -9`|`kill -9 1234`|
|PowerShell|`Stop-Process`|`Stop-Process -Id 1234`|
|CMD|`taskkill`|`taskkill /PID 1234 /F`|

Let me know if you want a script to automatically find and kill a process by name.

---

## References