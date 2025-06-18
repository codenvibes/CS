## What Are Signals?

Signals are a form of **inter-process communication (IPC)** used in Unix-like systems (like Linux). They allow the operating system and users to **communicate with processes** — typically to **interrupt**, **terminate**, **pause**, **resume**, or **inform** them of events.

- Signals are **asynchronous**: they can be sent at any time, not necessarily when the target process is "ready".
- Each signal has a **name** (e.g., `SIGTERM`) and a **number** (e.g., `15`).
- Processes can **handle**, **ignore**, or **act upon** most signals.

---

## Signal Behavior

When a process receives a signal, it can:
1. **Perform the default action** (e.g., terminate).
2. **Catch the signal** with a signal handler function (only for some signals).
3. **Ignore the signal** (except for a few like `SIGKILL` and `SIGSTOP`).

Some signals **cannot be caught or ignored**, like:
- `SIGKILL` (9) – immediate termination
- `SIGSTOP` (19) – uncatchable stop/pause

---

## Common Signals and Their Uses

|Signal Name|Number|Description|Default Action|Typical Use Case|
|---|---|---|---|---|
|`SIGTERM`|15|Terminate|Terminate|Clean shutdown of processes|
|`SIGKILL`|9|Kill immediately (cannot be caught)|Terminate|Force stop unresponsive processes|
|`SIGINT`|2|Interrupt (like Ctrl + C)|Terminate|User interruption from keyboard|
|`SIGQUIT`|3|Quit and create core dump|Terminate + core dump|Debugging|
|`SIGHUP`|1|Hangup (terminal closed)|Terminate|Reload config files or restart daemons|
|`SIGSTOP`|19|Stop (pause, cannot be caught)|Stop|Suspend process (like Ctrl + Z)|
|`SIGTSTP`|20|Terminal stop (catchable Ctrl + Z)|Stop|Pause from terminal|
|`SIGCONT`|18|Continue a stopped process|Continue|Resume from `SIGSTOP` or `SIGTSTP`|
|`SIGUSR1`|10|User-defined signal 1|Terminate|Custom user-defined behaviors|
|`SIGUSR2`|12|User-defined signal 2|Terminate|Custom user-defined behaviors|
|`SIGALRM`|14|Timer signal from `alarm()`|Terminate|Timing events|
|`SIGCHLD`|17|Child stopped or exited|Ignore|Used by parents to track child processes|
|`SIGPIPE`|13|Broken pipe (writing to closed pipe)|Terminate|Prevent writing to dead readers in pipelines|
|`SIGWINCH`|28|Window size change|Ignore|Used by terminal applications|

---

## Signal Commands and Usage

### 1. Sending Signals

#### Using `kill` (by PID):

```bash
kill -SIGNAL PID
kill -9 1234         # Send SIGKILL
kill -15 1234        # Send SIGTERM (default)
```

#### Using `killall` (by process name):

```bash
killall -s SIGTERM firefox
```

#### Using `pkill` (pattern-based):

```bash
pkill -SIGINT python
```

#### Sending signals interactively:

- `Ctrl + C`: Sends `SIGINT`
- `Ctrl + Z`: Sends `SIGTSTP`
- `fg`, `bg`, `jobs`: Resume/switch foreground/background


### 2. Listing Signals

#### Using `kill -l`:

```bash
kill -l
```

Gives a list like:

```
 1) SIGHUP     2) SIGINT     3) SIGQUIT   ... 9) SIGKILL ...
```


### 3. Handling Signals in Scripts/Programs

In shell scripting or programming languages like Python or C, processes can **trap and handle signals**.

#### In Bash:

```bash
trap "echo 'Caught SIGINT! Cleaning up...'; exit" SIGINT

while true; do
  sleep 1
done
```

#### In Python:

```python
import signal
import sys

def handler(sig, frame):
    print("Caught SIGINT! Exiting cleanly.")
    sys.exit(0)

signal.signal(signal.SIGINT, handler)

while True:
    pass
```

---

## 🔹 Foreground vs. Background Jobs & Signals

When working in a terminal:

- Foreground jobs receive keyboard signals (`SIGINT`, `SIGTSTP`) directly.
    
- Background jobs do not receive these by default.
    

You can manage jobs using:

- `jobs` – List current background/paused jobs
    
- `fg %1` – Bring job 1 to the foreground
    
- `bg %1` – Resume job 1 in background
    
- `kill %1` – Send `SIGTERM` to job 1
    

---

## 🔹 Signal Summary Table

|Signal|Num|Catchable|Default Action|Keyboard Equivalent|
|---|---|---|---|---|
|`SIGTERM`|15|Yes|Terminate|–|
|`SIGKILL`|9|**No**|Immediate Terminate|–|
|`SIGINT`|2|Yes|Terminate|`Ctrl + C`|
|`SIGQUIT`|3|Yes|Core dump|`Ctrl + \`|
|`SIGTSTP`|20|Yes|Pause (stop)|`Ctrl + Z`|
|`SIGSTOP`|19|**No**|Pause (stop)|–|
|`SIGCONT`|18|Yes|Resume|–|
|`SIGHUP`|1|Yes|Terminate|–|

---

## 🛠️ Real-World Examples

### Reloading a service (like `nginx`) without stopping it:

```bash
kill -HUP $(pidof nginx)
```

### Gracefully stopping a background script:

```bash
kill -TERM <PID>
```

### Pausing and resuming a process:

```bash
kill -STOP <PID>   # Pause
kill -CONT <PID>   # Resume
```

---

## 🧠 Things to Remember

- **Prefer `SIGTERM` (15)** for clean shutdowns.
    
- **Use `SIGKILL` (9)** only when absolutely necessary — no cleanup happens.
    
- **`SIGSTOP` and `SIGKILL` cannot be caught or ignored**.
    
- Many daemons and services respond to **`SIGHUP`** by reloading config files.
    

---

Would you like a **printable PDF version**, **flashcards**, or example scripts to practice handling signals?
---

## References

