#Process_Management #System_Initialization #Linux


## Viewing Processes

[[ps]] 
[[top]]

---
## Managing Processes

[[kill]]

---

## How Do Processes Start?

When an operating system boots up, it must set up a structured environment for managing and running various applications. One of the core responsibilities of the OS is to handle processes — individual instances of running programs — and manage how they consume and share system resources like CPU, memory, and I/O.

To accomplish this, the OS uses **namespaces** and **process identifiers (PIDs)** to organize and isolate processes securely and efficiently.

### Namespaces

Namespaces are a fundamental feature of modern operating systems, especially Linux, used to isolate processes and control their access to system resources. They allow the OS to divide the system into isolated environments — you can think of these as slices of a cake. Each "slice" or namespace operates like a mini-environment, with its own subset of available resources.

Processes running within the same namespace can see and interact with one another, but are isolated from processes in other namespaces. This is crucial for **security and process separation**, particularly in containerized environments (like Docker), where you want one container’s processes to remain invisible and inaccessible to another.

In practical terms, namespaces allow different processes to:
- Have isolated views of the filesystem
- Use different network stacks
- See different sets of running processes (via PID namespaces)
- Control resource consumption independently


### The Role of PIDs

Each process on a Linux system is assigned a **Process Identifier (PID)**, which uniquely distinguishes it from other processes. The kernel uses these PIDs to manage and track processes efficiently.

- The process with **PID 0** is a special process. It is created by the kernel itself and is not a typical user-space process. It’s often referred to as the **swapper** or **idle** task.
- After this, **PID 1** is the first user-space process to be created — commonly the **init system**.



### systemd and the Init System

In modern Linux distributions such as Ubuntu, the init system is usually **`systemd`**, which plays a central role in system initialization and service management.

Here's what happens during system startup:
1. The computer powers on and loads the **BIOS or UEFI** firmware.
2. This firmware loads the **bootloader** (like GRUB), which then loads the **Linux kernel**.
3. The kernel initializes hardware and low-level components and then starts **PID 1**, which is `systemd`.

Once `systemd` starts:
- It acts as the **root process** of the entire user-space process tree.
- All other services, background daemons, and user programs are launched as **child processes of `systemd`**.
- Each child process receives its own PID and can run independently, though it remains under the overall control of `systemd`.

This hierarchy is essential for resource management and makes it easier to:
- Track running services
- Control startup behavior
- Gracefully stop or restart applications
- Monitor logs via `journalctl`


### Child Processes and Resource Sharing

When a new application or service is started on a Linux system, it typically becomes a **child process** of `systemd` (or whichever process spawned it). This child process runs independently but shares some environment settings and potentially resource limits defined by its parent.

This parent-child relationship between processes:
- Forms a **process tree**
- Allows better tracking and grouping of related processes
- Is vital for process cleanup and termination when services crash or are stopped

For example, if you launch the Firefox browser, it may spawn multiple processes: one for the main UI, others for rendering tabs, extensions, or GPU acceleration. These are all structured in a tree under a parent process.

---

## Getting Processes/Services to Start on Boot

Some applications can be started on the boot of the system that we own. For example, web servers, database servers or file transfer servers. This software is often critical and is often told to start during the boot-up of the system by administrators.

In this example, we're going to be telling the apache web server to be starting apache manually and then telling the system to launch apache2 on boot.

Enter the use of [[systemctl]] -- this command allows us to interact with the **systemd** process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: `systemctl [option] [service]`

For example, to tell apache to start up, we'll use `systemctl start apache2`. Seems simple enough, right? Same with if we wanted to stop apache, we'd just replace the `[option]` with stop (instead of start like we provided)

We can do four options with `systemctl`:

- Start
- Stop
- Enable
- Disable

---

## An Introduction to Backgrounding and Foregrounding in Linux

### What Are Foreground and Background Processes?

In Linux (and Unix-like systems), every command you run in a terminal starts a **process** — a running instance of a program.

These processes can run in **two modes**:
- **Foreground**:
    - You interact with the program directly in the terminal.
    - You see all its output.
    - You can’t type or run anything else until the process finishes or you interrupt it.
- **Background**:
    - The program runs behind the scenes.
    - You don’t see the output (unless you redirect it).
    - Your terminal remains usable — you can type other commands.


### How to Run Processes in the Background

#### Method 1: Use the `&` symbol

If you add an `&` at the end of any command, Linux starts that process in the **background**.

#### Example:

```bash
echo "Hi THM" &
```

Instead of:

```
Hi THM
```

You get:

```
[1] 12345
```

- `12345` is the Process ID (PID).
- `[1]` is the job number.

This tells you: “Job 1 is now running in the background as process 12345.”

But here's the catch: you **don’t see the output** in your terminal. The shell starts the process but doesn't tie the output to your screen, so nothing is printed.


#### Method 2: Suspend a foreground job with `Ctrl + Z`, then background it with `bg`

When you run a command (e.g., a looping script), it's in the foreground. If it's overwhelming or long-running, you can **pause** it without stopping it using:

```bash
Ctrl + Z
```

You’ll see something like:

```
^Z
[1]+  Stopped   ./script.sh
```

This means the job is paused (status: _Stopped_). You can now:

Foreground it** again with:
```bash
fg
```

Resume it in the background** with:
```bash
bg
```

The command continues running in the background **from where it left off**.


### What Happens When You Use `&`?

Let’s understand the internals a bit:

When you run:

```bash
some_command &
```

Three key things happen:

1. The shell **forks** the process — it creates a child process to run the command.
2. That child process is **disassociated** from the terminal input/output — so it doesn’t "talk back" to the screen.
3. The shell immediately **returns control to you**, showing you the PID.

So if you're running something like:

```bash
cp largefile.txt /destination/ &
```

You don’t have to wait for the copy to finish — you can go on and run other commands.

If you don’t redirect output (`> file.txt`), the background process might still write messages to your terminal, especially if there are errors.


### Using `Ctrl + Z` to Suspend a Foreground Process

Let’s say you have a script that loops forever:

```bash
while true; do echo "looping"; sleep 1; done
```

When you run this, it fills your terminal with output.

#### To pause (suspend) it:

Press:

```bash
Ctrl + Z
```

This sends a **SIGTSTP** signal to the process, telling it to "stop temporarily."

The shell responds with something like:

```
┌──(mopsy㉿APHP)-[~]
└─$ while true; do echo "looping"; sleep 1; done
looping
looping
looping
looping
^Z
[2]+  Stopped                 sleep 1
```

Now the process is no longer flooding your terminal — it’s frozen in RAM, not terminated.



### Managing Jobs with `jobs`, `fg`, and `bg`

Once you’ve suspended or backgrounded a job, you can manage it.

#### View active jobs:

```bash
jobs
```

Example output:

```
┌──(mopsy㉿APHP)-[~]
└─$ jobs
[1]-  Stopped                 sleep 1
[2]+  Stopped                 sleep 1
```

#### Bring a job back to the foreground:

```bash
fg %1
```

This brings job number 1 to the foreground. If you leave out `%1`, `fg` defaults to the last job.

#### Continue a job in the background:

```bash
bg %1
```

This resumes a **stopped** job and puts it in the background.

#### Terminate a job:

- From foreground: `Ctrl + C` (sends SIGINT)
- From background: use `kill`, e.g.:
    
    ```bash
    kill %1
    ```
    

Or kill by PID:

```bash
kill 12345
```


### Why Does This Matter?

Here’s when backgrounding processes is useful:

- **Long-running commands**: Background them and keep using the terminal.
- **Running scripts or servers**: Don’t let them block your session.
- **Pausing a command**: Suspend it and decide later if you want to kill or resume it.

It’s especially handy in **Linux server environments**, where you might be managing multiple processes from a single terminal.


---

## References

https://tryhackme.com/room/linuxfundamentalspart3