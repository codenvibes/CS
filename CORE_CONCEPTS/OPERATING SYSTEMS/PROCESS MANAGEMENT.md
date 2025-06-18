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

Processes can run in two states: In the background and in the foreground. For example, commands that you run in your terminal such as "echo" or things of that sort will run in the foreground of your terminal as it is the only command provided that hasn't been told to run in the background. "Echo" is a great example as the output of echo will return to you in the foreground, but wouldn't in the background - take the screenshot below, for example.

![](https://assets.tryhackme.com/additional/linux-fundamentals/part3/bg1.png)  

Here we're running `echo "Hi THM"` , where we expect the output to be returned to us like it is at the start. But after adding the `&` operator to the command, we're instead just given the ID of the echo process rather than the actual output -- as it is running in the background.

This is great for commands such as copying files because it means that we can run the command in the background and continue on with whatever further commands we wish to execute (without having to wait for the file copy to finish first)

We can do the exact same when executing things like scripts -- rather than relying on the & operator, we can use `Ctrl + Z` on our keyboard to background a process. It is also an effective way of "pausing" the execution of a script or command like in the example below:

![](https://assets.tryhackme.com/additional/linux-fundamentals/part3/bg2.png)  

This script will keep on repeating "This will keep on looping until I stop!" until I stop or suspend the process. By using `Ctrl + Z` (as indicated by **T^Z**). Now our terminal is no longer filled up with messages -- until we foreground it, which we will discuss below.

  

**Foregrounding a process**

Now that we have a process running in the background, for example, our script "background.sh" which can be confirmed by using the `ps aux` command, we can back-pedal and bring this process back to the foreground to interact with.

![](https://assets.tryhackme.com/additional/linux-fundamentals/part3/bg3.png)  

With our process backgrounded using either `Ctrl + Z` or the `&` operator, we can use `fg` to bring this back to focus like below, where we can see the `fg` command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.

![](https://assets.tryhackme.com/additional/linux-fundamentals/part3/bg4.png)

![](https://assets.tryhackme.com/additional/linux-fundamentals/part3/bg5.png)

---

## References

https://tryhackme.com/room/linuxfundamentalspart3