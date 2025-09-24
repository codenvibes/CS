---
tags:
  - COMMAND_LINE
aliases:
---
## 1. Introduction

Everyone prefers a graphical user interface (GUI) until they master a command-line interface (CLI). There are many reasons for that. One reason is that GUIs are usually intuitive. If someone offers you a GUI interface you are unfamiliar with, you can quickly poke around and discover a non-trivial part. Compare this with dealing with a CLI, i.e., a prompt.

CLI interfaces usually have a learning curve; however, as you master the command line, you will find it faster and more efficient. Consider this trivial example: How many clicks do you need to find your IP address using the graphical desktop? Using the command-line interface, you don’t even need to raise your hands off the keyboard. Let’s say you want to recheck your IP address. You need to issue the same command instead of moving the mouse pointer to every corner of your screen.

There are many other advantages to using a CLI besides speed and efficiency. We will mention a few:

- **Lower resource usage**: CLIs require fewer system resources than graphics-intensive GUIs. In other words, you can run your CLI system on older hardware or systems with limited memory. If you are using cloud computing, your system will require lower resources, which in turn will lower your bill.
- **Automation**: While you can automate GUI tasks, creating a batch file or script with the commands you need to repeat is much easier.
- **Remote management**: CLI makes it very convenient to use SSH to manage a remote system such as a server, router, or an IoT device. This approach works well on slow network speeds and systems with limited resources.
<div>
<br>
</div>

### Learning Objectives

The purpose of this room is to teach you how to use MS Windows Command Prompt `cmd.exe`, the default command-line interpreter in the Windows environment. We will learn how to use the command line to:

- Display basic system information
- Check and troubleshoot network configuration
- Manage files and folders
- Check running processes
<div>
<br>
</div>

### Room Prerequisites

Before starting this room, you should have finished the [Windows and AD Fundamentals](https://tryhackme.com/module/windows-and-active-directory-fundamentals) module.

Press the **Start Machine** button below.

Start the AttackBox by pressing the **Start AttackBox** button at the top of this page. The AttackBox machine will start in Split-Screen view. If it is not visible, use the blue **Show Split View** button at the top of the page.

You can use the SSH client on the AttackBox to connect to `MACHINE_IP` with the following credentials:

- Username: `user`
- Password: `Tryhackme123!`
<div>
<br>
</div>

### Establishing an SSH Connection from the AttackBox

If this is the first time you initiate an SSH connection from the AttackBox to a target system, the steps are shown in the screenshot below, and they are the following:

1. Start the AttackBox’s terminal by clicking the terminal icon marked with 1.
2. To connect to the target VM, issue the command `ssh user@MACHINE_IP` as `user` is the username in this case.
3. Because this is your first time connecting to this target VM, you will be asked to trust this connection. Answer with **yes** as marked with 3.
4. Enter your password `Tryhackme123!`. Please note that the password will not appear as you type it.

![Starting the terminal on the AttackBox and connecting the target VM using SSH.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1724312337656.png)
<div>
<br>
<br>
</div>

### Questions

##### What is the default command line interpreter in the Windows environment?
cmd.exe
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. Basic System Information

Before issuing commands, we should note that we can only issue the commands within the Windows Path. You can issue the command `set` to check your path from the command line. The terminal output below shows the path where MS Windows will execute commands, as indicated by the line starting with `Path=`.

```shell-session
C:\>set
ALLUSERSPROFILE=C:\ProgramData
[...]
LOGNAME=strategos
NUMBER_OF_PROCESSORS=2
OS=Windows_NT
Path=C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Windows\system32\config\systemprofile\AppData\Local\Microsoft\WindowsApps;C:\Users\strategos\AppData\Local\Microsoft\WindowsApps;
[...]
```

Let’s use the `ver` command to determine the operating system (OS) version. The terminal below shows an example output.

```shell-session
C:\>ver                                                                                                                                              
Microsoft Windows [Version 10.0.17763.1821]
```

Enough warming up. Let’s discover more in-depth information about the system. We can run the `systeminfo` command to list various information about the system such as OS information, system details, processor and memory. The terminal below shows a snippet of the displayed output.

```shell-session
C:\>systeminfo

Host Name:                 WIN-SRV-2019
OS Name:                   Microsoft Windows Server 2019 Datacenter
OS Version:                10.0.17763 N/A Build 17763
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
[...]
```

Before moving on, it is good to mention a couple of tricks.

First, you can pipe it through `more` if the output is too long. Then, you can view it page after page by pressing the space bar button. To demonstrate this, try running `driverquery` and compare it with running `driverquery | more`. In the latter, you can display the output page by page and you can exit it using `CTRL + C`.

- `help` - Provides help information for a specific command
- `cls` - Clears the Command Prompt screen.
<div>
<br>
<br>
</div>

### Questions

##### What is the OS version of the Windows VM?
##### What is the hostname of the Windows VM?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Network Troubleshooting
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. File and Disk Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Task and Process Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Conclusion
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/windowscommandline