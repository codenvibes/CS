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

Enter the use of `systemctl` -- this command allows us to interact with the **systemd** process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: `systemctl [option] [service]`

For example, to tell apache to start up, we'll use `systemctl start apache2`. Seems simple enough, right? Same with if we wanted to stop apache, we'd just replace the `[option]` with stop (instead of start like we provided)

We can do four options with `systemctl`:

- Start
- Stop
- Enable
- Disable


---

## References

https://tryhackme.com/room/linuxfundamentalspart3