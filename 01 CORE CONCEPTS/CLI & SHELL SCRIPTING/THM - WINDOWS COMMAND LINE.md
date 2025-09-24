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
10.0.20348.2655

```
user@WINSRV2022-CORE C:\Users\user>ver

Microsoft Windows [Version 10.0.20348.2655]
```
<div>
<br>
</div>

##### What is the hostname of the Windows VM?
WINSRV2022-CORE

```
user@WINSRV2022-CORE C:\Users\user>systeminfo

Host Name:                 WINSRV2022-CORE
OS Name:                   Microsoft Windows Server 2022 Datacenter
OS Version:                10.0.20348 N/A Build 20348
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
Registered Owner:          Windows User
Registered Organization:   
Product ID:                00454-60000-00001-AA763
Original Install Date:     4/23/2024, 7:36:29 PM
System Boot Time:          9/24/2025, 6:48:44 AM
System Manufacturer:       Amazon EC2
System Model:              t3.small
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 85 Stepping 7 GenuineIntel ~2500 Mhz
BIOS Version:              Amazon EC2 1.0, 10/16/2017
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC+00:00) Dublin, Edinburgh, Lisbon, London        
Total Physical Memory:     1,894 MB
Available Physical Memory: 1,104 MB
Virtual Memory: Max Size:  2,214 MB
Virtual Memory: Available: 1,421 MB
Virtual Memory: In Use:    793 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              N/A
Hotfix(s):                 3 Hotfix(s) Installed.
                           [01]: KB5041948
                           [02]: KB5041160
                           [03]: KB5041590
Network Card(s):           1 NIC(s) Installed.
                           [01]: Amazon Elastic Network Adapter
                                 Connection Name: Ethernet
                                 DHCP Enabled:    Yes
                                 DHCP Server:     10.10.0.1
                                 IP address(es)
                                 [01]: 10.10.121.185
                                 [02]: fe80::e2db:a0a1:986c:3834
Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.
```
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Network Troubleshooting

Most of us are used to looking up MS Windows network configuration from the GUI interface. The command-line interface provides many networking-related commands to look up your current configuration, check ongoing connections, and troubleshoot networking issues.

### Network Configuration

You can check your network information using `ipconfig`. The terminal output below shows our IP address, subnet mask, and default gateway.

Terminal

```shell-session
C:\>ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Link-local IPv6 Address . . . . . : fe80::90df:4861:ba40:f2a8%4
   IPv4 Address. . . . . . . . . . . : 10.10.230.237
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 10.10.0.1
```

You can also use `ipconfig /all` for more information about your network configuration. As shown in the terminal below, we can view our DNS servers and confirm that DHCP is enabled.

Terminal

```shell-session
C:\>ipconfig /all

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Description . . . . . . . . . . . : Amazon Elastic Network Adapter
   Physical Address. . . . . . . . . : 02-B7-DF-1D-0D-99
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::90df:4861:ba40:f2a8%4(Preferred) 
   IPv4 Address. . . . . . . . . . . : 10.10.230.237(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Lease Obtained. . . . . . . . . . : Wednesday, May 1, 2024 2:38:05 PM
   Lease Expires . . . . . . . . . . : Wednesday, May 1, 2024 4:08:07 PM
   Default Gateway . . . . . . . . . : 10.10.0.1
   DHCP Server . . . . . . . . . . . : 10.10.0.1
   DHCPv6 IAID . . . . . . . . . . . : 134353458
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-27-E3-D1-2B-0E-F8-30-D0-72-3F
   DNS Servers . . . . . . . . . . . : 10.0.0.2
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

### Network Troubleshooting

One common troubleshooting task is checking if the server can access a particular server on the Internet. The command syntax is `ping target_name`. Inspired by ping-pong, we send a specific ICMP packet and listen for a response. If a response is received, we know that we can reach the target and that the target can reach us.

Let’s find out if we reach `example.com`. In the terminal output below, we can see that we have successfully received four replies. Furthermore, we got some statistics; for instance, the average round trip time is 78 milliseconds.

Terminal

```shell-session
C:\>ping example.com

Pinging example.com [93.184.215.14] with 32 bytes of data:
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52

Ping statistics for 93.184.215.14:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 78ms, Maximum = 78ms, Average = 78ms
```

Another valuable tool for troubleshooting is `tracert`, which stands for _trace route_. The command `tracert target_name` traces the network route traversed to reach the target. Without getting into more details, it expects the routers on the path to notify us if they drop a packet because its time-to-live (TTL) has reached zero. The terminal output below shows that we passed through 15 routers before reaching our target.

Terminal

```shell-session
C:\>tracert example.com

Tracing route to example.com [93.184.215.14]
over a maximum of 30 hops:

  1    59 ms    32 ms    42 ms  ec2-3-248-240-3.eu-west-1.compute.amazonaws.com [3.248.240.3]
  2     *        *        *     Request timed out.
  3     *        *        *     Request timed out.
  4     *        *        *     Request timed out.
  5     *        *        *     Request timed out.
  6     *        *        *     Request timed out.
  7     *        *        *     Request timed out.
  8     *        *        *     Request timed out.
  9    <1 ms    13 ms    <1 ms  100.100.2.56
 10    15 ms    11 ms    11 ms  ae-42.a03.londen12.uk.bb.gin.ntt.net [131.103.117.104]
 11    17 ms    11 ms    12 ms  ae-14.r20.londen12.uk.bb.gin.ntt.net [129.250.3.248]
 12    81 ms    80 ms    80 ms  ae-7.r20.nwrknj03.us.bb.gin.ntt.net [129.250.6.147]
 13    83 ms    83 ms    86 ms  ae-0.a02.nycmny17.us.bb.gin.ntt.net [129.250.3.9]
 14    79 ms    79 ms    96 ms  ce-0-3-0.a02.nycmny17.us.ce.gin.ntt.net [128.241.1.14]
 15    81 ms    86 ms    79 ms  ae-67.core1.nyd.edgecastcdn.net [152.195.68.135]
 16    78 ms    78 ms    78 ms  93.184.215.14

Trace complete.
```

### More Networking Commands

One networking command worth knowing is `nslookup`. It looks up a host or domain and returns its IP address. The syntax `nslookup example.com` will look up `example.com` using the default name server; however, `nslookup example.com 1.1.1.1` will use the name server `one.one.one.one`. The terminal below shows the output of both commands. The results are identical; however, you can see that the answers were retrieved from different name servers.

Terminal

```shell-session
C:\>nslookup example.com
Server:  ip-10-0-0-2.eu-west-1.compute.internal
Address:  10.0.0.2

Non-authoritative answer:
Name:    example.com
Addresses:  2606:2800:21f:cb07:6820:80da:af6b:8b2c
          93.184.215.14

C:>nslookup example.com 1.1.1.1
Server:  one.one.one.one
Address:  1.1.1.1

Non-authoritative answer:
Name:    example.com
Addresses:  2606:2800:21f:cb07:6820:80da:af6b:8b2c
          93.184.215.14
```

The final networking command we will cover in this room is `netstat`. This command displays current network connections and listening ports. A basic `netstat` command with no arguments will show you established connections, as shown below. In this case, we only have one SSH connection; we figured out it is SSH because it is bound to port 22.

Terminal

```shell-session
C:\>netstat

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    10.10.230.237:22       ip-10-11-81-126:53486  ESTABLISHED
```

If you are curious about the other options, you can run `netstat -h`, where `-h` displays the help page. We opted for the following options:

- `-a` displays all established connections and listening ports
- `-b` shows the program associated with each listening port and established connection
- `-o` reveals the process ID (PID) associated with the connection
- `-n` uses a numerical form for addresses and port numbers

We combine these four options and execute the `netstat -abon` command. The result is quite long, but we display the first few lines in the terminal below. It is clear now that the executable `sshd.exe` is responsible for listening for incoming connections on port 22, as shown in the first line. We can also see the process ID (PID) associated with each connection.

Terminal

```shell-session
C:\>netstat -abon

Active Connections

  Proto  Local Address          Foreign Address        State           PID 
  TCP    0.0.0.0:22             0.0.0.0:0              LISTENING       2116
 [sshd.exe]
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       820
  RpcSs 
 [svchost.exe]
[...]
  TCP    0.0.0.0:49669          0.0.0.0:0              LISTENING       2036
 [spoolsv.exe]
  TCP    0.0.0.0:49670          0.0.0.0:0              LISTENING       584 
 Can not obtain ownership information
  TCP    0.0.0.0:49686          0.0.0.0:0              LISTENING       592
 [lsass.exe]
  TCP    10.10.230.237:22       10.11.81.126:53486     ESTABLISHED     2116 
 [sshd.exe]
 [...]
```
<div>
<br>
<br>
</div>

### Questions

##### 
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