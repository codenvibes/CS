#THM 
## WINDOWS FORENSICS 1

### 1. Introduction to Windows Forensics

**Digital forensics** involves recovering and analyzing data from digital devices to investigate cyber incidents or crimes. **Computer forensics**, a subset, focuses on analyzing evidence from computers. It’s used in both legal cases and private investigations.

A perfect example of Digital Forensics solving a criminal case is the [BTK serial killer](https://en.wikipedia.org/wiki/Dennis_Rader) case. This case had gone cold for more than a decade when the killer started taunting the police by sending letters. The case took a major turn when he sent a floppy disk to a local news station that was later taken to into evidence by the police. The police were able to recover a deleted word document on the drive, and using the metadata and some other evidence, they pinpointed and arrested him.

Because **Windows dominates the desktop OS market**, it’s vital for forensic analysts to understand how to extract evidence from it—especially using data from the **Windows Registry**.

#### DEF-Forensic Artifacts:

==An **artifact** is any piece of data or evidence left behind on a digital device that can help investigators understand what happened on that system. Just like fingerprints at a physical crime scene, digital artifacts are clues that help reconstruct the actions of a user or attacker on a computer or network.==

Artifacts can include:
- Browser history
- Log files
- Installed applications
- Deleted files
- Timestamps (like last login time)
- Registry entries (on Windows)
- System event logs

In computer forensics, forensic artifacts can be small footprints of activity left on the computer system. On a Windows system, a person's actions can be traced back quite accurately using computer forensics because of the various artifacts a Windows system creates for a given activity. These artifacts often reside in locations 'normal' users won't typically venture to. For our purposes, these artifacts can be analyzed to provide the trial of activity for an investigation.

#### Questions

![[Pasted image 20250728184827.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 2. Windows Registry and Forensics

#### Windows Registry:

The Windows Registry is a collection of databases that contains the system's configuration data. This configuration data can be about the hardware, the software, or the user's information. It also includes data about the recently used files, programs used, or devices connected to the system. As you can understand, this data is beneficial from a forensics standpoint. Throughout this room, we will learn ways to read this data to identify the required information about the system. You can view the registry using regedit.exe, a built-in Windows utility to view and edit the registry. We'll explore other tools to learn about the registry in the upcoming tasks.

The Windows registry consists of Keys and Values. When you open the regedit.exe utility to view the registry, the folders you see are Registry Keys. Registry Values are the data stored in these Registry Keys. 

A [Registry Hive](https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry-hives#:~:text=Registry%20Hives.%20A%20hive%20is%20a%20logical%20group,with%20a%20separate%20file%20for%20the%20user%20profile.) is a group of Keys, subkeys, and values stored in a single file on the disk.

#### Structure of the Registry:

The registry on any Windows system contains the following five root keys:

1. HKEY_CURRENT_USER
2. HKEY_USERS
3. HKEY_LOCAL_MACHINE
4. HKEY_CLASSES_ROOT
5. HKEY_CURRENT_CONFIG

You can view these keys when you open the `regedit.exe` utility. To open the registry editor, press the Windows key and the R key simultaneously. It will open a `run` prompt that looks like this:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/9d33389f2fd0445a63e75dce3f6d7a88.png)

In this prompt, type `regedit.exe` , and you will be greeted with the registry editor window. It will look something like this:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/e14ef3193fce1f4b35c37a96862d71da.png)

Here you can see the root keys in the left pane in a tree view that shows the included registry keys, and the values in the selected key are shown in the right pane. You can right-click on the value shown in the right pane and select properties to view the properties of this value.

Here is how Microsoft defines each of these root keys. For more detail and information about the following Windows registry keys, please visit  [Microsoft's documentation](https://docs.microsoft.com/en-US/troubleshoot/windows-server/performance/windows-registry-advanced-users) .

| Folder/predefined key   |                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **HKEY_CURRENT_USER**   | settings for the current user                                       | Contains the root of the configuration information for the user who is currently logged on. The user's folders, screen colors, and Control Panel settings are stored here. This information is associated with the user's profile. This key is sometimes abbreviated as HKCU.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **HKEY_USERS**          | profiles for all users                                              | Contains all the actively loaded user profiles on the computer. HKEY_CURRENT_USER is a subkey of HKEY_USERS. HKEY_USERS is sometimes abbreviated as HKU.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **HKEY_LOCAL_MACHINE**  | settings for the entire system                                      | Contains configuration information particular to the computer (for any user). This key is sometimes abbreviated as HKLM.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **HKEY_CLASSES_ROOT**   | This hive defines which program should handle which file extension. | Is a subkey of `HKEY_LOCAL_MACHINE\Software` . The information that is stored here makes sure that the correct program opens when you open a file by using Windows Explorer. This key is sometimes abbreviated as HKCR.<br><br>Starting with Windows 2000, this information is stored under both the HKEY_LOCAL_MACHINE and HKEY_CURRENT_USER keys. The `HKEY_LOCAL_MACHINE\Software\Classes` key contains default settings that can apply to all users on the local computer.  The `HKEY_CURRENT_USER\Software\Classes` key has settings that override the default settings and apply only to the interactive user.<br><br>The HKEY_CLASSES_ROOT key provides a view of the registry that merges the information from these two sources. HKEY_CLASSES_ROOT also provides this merged view for programs that are designed for earlier versions of Windows. To change the settings for the interactive user, changes must be made under `HKEY_CURRENT_USER\Software\Classes` instead of under HKEY_CLASSES_ROOT.<br><br>To change the default settings, changes must be made under `HKEY_LOCAL_MACHINE\Software\Classes`  .If you write keys to a key under HKEY_CLASSES_ROOT, the system stores the information under `HKEY_LOCAL_MACHINE\Software\Classes` .<br><br>If you write values to a key under HKEY_CLASSES_ROOT, and the key already exists under `HKEY_CURRENT_USER\Software\Classes` , the system will store the information there instead of under `HKEY_LOCAL_MACHINE\Software\Classes` . |
| **HKEY_CURRENT_CONFIG** | hardware profile in use                                             | Contains information about the hardware profile that is used by the local computer at system startup.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
#### Questions

![[Pasted image 20250728185001.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 3. Accessing registry hives offline

If you are accessing a live system, you will be able to access the registry using regedit.exe, and you will be greeted with all of the standard root keys we learned about in the previous task. 

However, if you only have access to a disk image, you must know where the registry hives are located on the disk. The majority of these hives are located in the `C:\Windows\System32\Config` directory and are:

| Hive Name    | Mounted On                    | Description                                                                                |
| ------------ | ----------------------------- | ------------------------------------------------------------------------------------------ |
| **DEFAULT**  | `HKEY_USERS\DEFAULT`          | Default profile settings used when no user is logged in.                                   |
| **SAM**      | `HKEY_LOCAL_MACHINE\SAM`      | **SAM** stands for **Security Account Manager**. Stores user account info and credentials. |
| **SECURITY** | `HKEY_LOCAL_MACHINE\SECURITY` | Holds local security policies and settings.                                                |
| **SOFTWARE** | `HKEY_LOCAL_MACHINE\SOFTWARE` | Installed software and configuration data.                                                 |
| **SYSTEM**   | `HKEY_LOCAL_MACHINE\SYSTEM`   | System settings, drivers, services, and startup info.                                      |

#### Hives containing user information:

Apart from these hives, two other hives containing user information can be found in the User profile directory. For Windows 7 and above, a user’s profile directory is located in `C:\Users\<username>\` where the hives are:

| Hive Name        | Mounted On                           | Location                                               | Description                                                  |
| ---------------- | ------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------------ |
| **NTUSER.DAT**   | `HKEY_CURRENT_USER`                  | `C:\Users\<username>\`                                 | User profile settings and preferences.                       |
| **USRCLASS.DAT** | `HKEY_CURRENT_USER\Software\Classes` | `C:\Users\<username>\AppData\Local\Microsoft\Windows\` | User-specific file associations and COM class registrations. |

The USRCLASS.DAT hive is located in the directory `C:\Users\<username>\AppData\Local\Microsoft\Windows`. 

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/3ffadf20ebe241040d659958db115c2f.png)  

The NTUSER.DAT hive is located in the directory `C:\Users\<username>\`.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/f3091f38f680b418f89cf79128d1933c.png)

Remember that NTUSER.DAT and USRCLASS.DAT are hidden files.

#### The Amcache Hive:

Apart from these files, there is another very important hive called the AmCache hive. This hive is located in `C:\Windows\AppCompat\Programs\Amcache.hve`. Windows creates this hive to save information on programs that were recently run on the system.

#### Transaction Logs and Backups:

Some other very vital sources of forensic data are the registry transaction logs and backups. The transaction logs can be considered as the journal of the changelog of the registry hive. Windows often uses transaction logs when writing data to registry hives. This means that the transaction logs can often have the latest changes in the registry that haven't made their way to the registry hives themselves. The transaction log for each hive is stored as a .LOG file in the same directory as the hive itself. It has the same name as the registry hive, but the extension is .LOG. For example, the transaction log for the SAM hive will be located in `C:\Windows\System32\Config` in the filename SAM.LOG. Sometimes there can be multiple transaction logs as well. In that case, they will have .LOG1, .LOG2 etc., as their extension. It is prudent to look at the transaction logs as well when performing registry forensics.

Registry backups are the opposite of Transaction logs. These are the backups of the registry hives located in the `C:\Windows\System32\Config` directory. These hives are copied to the `C:\Windows\System32\Config\RegBack` directory every ten days. It might be an excellent place to look if you suspect that some registry keys might have been deleted/modified recently.

#### Questions

![[Pasted image 20250728192904.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 4. Data Acquisition

When performing forensics, we will either encounter a live system or an image taken of the system. For the sake of accuracy, it is recommended practice to image the system or make a copy of the required data and perform forensics on it. This process is called data acquisition. Below we discuss different ways to acquire registry data from a live system or a disk image:

Though we can view the registry through the registry editor, the forensically correct method is to acquire a copy of this data and perform analysis on that. However, when we go to copy the registry hives from `%WINDIR%\System32\Config` , we cannot because it is a restricted file. So, what to do now?

For acquiring these files, we can use one of the following tools:

#### KAPE

[KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) is a live data acquisition and analysis tool which can be used to acquire registry data. It is primarily a command-line tool but also comes with a GUI. The below screenshot shows what the KAPE GUI looks like. We have already selected all the settings to extract the registry data using KAPE in this screenshot. We will learn more about collecting forensic artifacts using KAPE in a dedicated KAPE room.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/48b9656c4037d0537bf517d6084517a8.png)

#### Autopsy

[Autopsy](https://www.autopsy.com/)  gives you the option to acquire data from both live systems or from a disk image. After adding your data source, navigate to the location of the files you want to extract, then right-click and select the Extract File(s) option. It will look similar to what you see in the screenshot below.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/5faf350078f7e7e1d1400f46e11e74a9.png)

#### FTK Imager

[FTK Imager](https://www.exterro.com/ftk-imager)  is similar to Autopsy and allows you to extract files from a disk image or a live system by mounting the said disk image or drive in FTK Imager. Below you can see the option to Export files as highlighted in the screenshot.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/08b1f97dd47b33c4261fb362d49ac929.png)

Another way you can extract Registry files from FTK Imager is through the Obtain Protected Files option. This option is only available for live systems and is highlighted in the screenshot below. This option allows you to extract all the registry hives to a location of your choosing. However, it will not copy the `Amcache.hve` file, which is often necessary to investigate evidence of programs that were last executed.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/6aa5e6825bb003dc803106d5f70e155c.png)

For the purpose of this room, we will not be acquiring data ourselves, but instead, we will work with the attached VM that already has data.

#### Questions

![[Pasted image 20250728193754.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 5. Exploring Windows Registry

Once we have extracted the registry hives, we need a tool to view these files as we would in the registry editor. Since the registry editor only works with live systems and can't load exported hives, we can use the following tools:

#### Registry Viewer

As we can see in the screenshot below, [AccessData's Registry Viewer](https://accessdata.com/product-download/registry-viewer-2-0-0)  has a similar user interface to the Windows Registry Editor. There are a couple of limitations, though. It only loads one hive at a time, and it can't take the transaction logs into account.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/888afb265fa265d771dc02ae8f610dc0.png)

#### Zimmerman's Registry Explorer

Eric Zimmerman has developed a handful of [tools](https://ericzimmerman.github.io/#!index.md) that are very useful for performing Digital Forensics and Incident Response. One of them is the Registry Explorer. It looks like the below screenshot. It can load multiple hives simultaneously and add data from transaction logs into the hive to make a more 'cleaner' hive with more up-to-date data. It also has a handy 'Bookmarks' option containing forensically important registry keys often sought by forensics investigators. Investigators can go straight to the interesting registry keys and values with the bookmarks menu item. We will explore these in more detail in the upcoming tasks.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/414dee2639b9456334c9580aacdc2be1.png)  
  
#### RegRipper

[RegRipper](https://github.com/keydet89/RegRipper3.0) is a utility that takes a registry hive as input and outputs a report that extracts data from some of the forensically important keys and values in that hive. The output report is in a text file and shows all the results in sequential order. 

RegRipper is available in both a CLI and GUI form which is shown in the screenshot below.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/70e6fef3920cb9b0443bc1fa9d9fac5d.png)

One shortcoming of RegRipper is that it does not take the transaction logs into account. We must use Registry Explorer to merge transaction logs with the respective registry hives before sending the output to RegRipper for a more accurate result.

Even though we have discussed these different tools, for the purpose of this room, we will only be using Registry Explorer and some of Eric Zimmerman's tools. The other tools mentioned here will be covered in separate rooms.

#### Questions

![[Pasted image 20250728194314.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 6. System Information and System Accounts

Now that we have learned how to read registry data, let's find out where to look in the registry to perform our forensic analysis.

When we start performing forensic analysis, the first step is to find out about the system information. This task will cover gathering information related to a machine's System and Account information.

#### OS Version

If we only have triage data to perform forensics, we can determine the OS version from which this data was pulled through the registry. To find the OS version, we can use the following registry key:

`SOFTWARE\Microsoft\Windows NT\CurrentVersion`

This is how Registry Explorer shows this registry key. Take a look and answer Question # 1.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/1362c5a15d1879a1a5a5a5237a426108.png)    

#### Current control set

The hives containing the machine’s configuration data used for controlling system startup are called Control Sets. Commonly, we will see two Control Sets, ControlSet001 and ControlSet002, in the SYSTEM hive on a machine. In most cases (but not always), ControlSet001 will point to the Control Set that the machine booted with, and ControlSet002 will be the `last known good`  configuration. Their locations will be:

`SYSTEM\ControlSet001`

`SYSTEM\ControlSet002`

Windows creates a volatile Control Set when the machine is live, called the CurrentControlSet ( `HKLM\SYSTEM\CurrentControlSet` ). For getting the most accurate system information, this is the hive that we will refer to. We can find out which Control Set is being used as the CurrentControlSet by looking at the following registry value:

`SYSTEM\Select\Current`

Similarly, the `last known good` configuration can be found using the following registry value:

`SYSTEM\Select\LastKnownGood`

This is how it looks like in Registry Explorer. Take a look and answer Question # 2.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/f3b34b5e44e98e76034b76fc608a7670.png)

It is vital to establish this information before moving forward with the analysis. As we will see, many forensic artifacts we collect will be collected from the Control Sets.

#### Computer Name:

It is crucial to establish the Computer Name while performing forensic analysis to ensure that we are working on the machine we are supposed to work on. We can find the Computer Name from the following location:

`SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`  

Registry Explorer shows it like this. Take a look and answer Question # 3:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/bb73d7942a6e30cb96e78926ad36fddb.png)

#### Time Zone Information

For accuracy, it is important to establish what time zone the computer is located in. This will help us understand the chronology of the events as they happened. For finding the Time Zone Information, we can look at the following location:

`SYSTEM\CurrentControlSet\Control\TimeZoneInformation`

Here's how it looks in Registry Explorer. Take a look and answer Question # 4.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/08d5e86bb3a5be6057928a8062cf7de3.png)

Time Zone Information is important because some data in the computer will have their timestamps in UTC/GMT and others in the local time zone. Knowledge of the local time zone helps in establishing a timeline when merging data from all the sources.

#### Network Interfaces and Past Networks:

The following registry key will give a list of network interfaces on the machine we are investigating:

`SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces`

Take a look at this registry key as shown in Registry Explorer and answer Question # 5.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/7f0ed33ad442f22ec9475488d6af4421.png)  
  

Each Interface is represented with a unique identifier (GUID) subkey, which contains values relating to the interface’s TCP/IP configuration. This key will provide us with information like IP addresses, DHCP IP address and Subnet Mask, DNS Servers, and more. This information is significant because it helps you make sure that you are performing forensics on the machine that you are supposed to perform it on.

The past networks a given machine was connected to can be found in the following locations:

`SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Unmanaged`

`SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Managed   `

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/fae511770c0ac57458073992ef221251.png)

These registry keys contain past networks as well as the last time they were connected. The last write time of the registry key points to the last time these networks were connected.

#### Autostart Programs (Autoruns)

The following registry keys include information about programs or commands that run when a user logs on. 

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`

`SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`

`SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run`

`SOFTWARE\Microsoft\Windows\CurrentVersion\Run`

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/6745df01d5c2f896795d5d6f481461b7.png)

The following registry key contains information about services:

`SYSTEM\CurrentControlSet\Services`

Notice the Value of the Start key in the screenshot below.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/5605bfda34393bfcb8c4aee6a5ad771f.png)

In this registry key, if the `start`   key is set to 0x02, this means that this service will start at boot.

#### SAM hive and user information:

The SAM hive contains user account information, login information, and group information. This information is mainly located in the following location:

`SAM\Domains\Account\Users`

Take a look at the below screenshot and answer Question # 6.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/d24056c00af7ef9e77ea25b883cdf06c.png)

The information contained here includes the relative identifier (RID) of the user, number of times the user logged in, last login time, last failed login, last password change, password expiry, password policy and password hint, and any groups that the user is a part of.

#### Questions

![[Pasted image 20250728203926.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 7. Usage or knowledge of files/folders

#### Recent Files

Windows maintains a list of recently opened files for each user. As we might have seen when using Windows Explorer, it shows us a list of recently used files.  This information is stored in the NTUSER hive and can be found on the following location:

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs`

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/aff5ea8e993f2989f5f8caf94798a3c7.png)

Registry Explorer allows us to sort data contained in registry keys quickly. For example, the Recent documents tab arranges the Most Recently Used (MRU) file at the top of the list. Registry Explorer also arranges them so that the Most Recently Used (MRU) file is shown at the top of the list and the older ones later.

Another interesting piece of information in this registry key is that there are different keys with file extensions, such as  `.pdf` , `.jpg` , `.docx`  etc. These keys provide us with information about the last used files of a specific file extension. So if we are looking specifically for the last used PDF files, we can look at the following registry key:

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.pdf`

Registry Explorer also lists the Last Opened time of the files. Answer Question # 1 by looking at the above screenshot.

#### Office Recent Files

Similar to the Recent Docs maintained by Windows Explorer, Microsoft Office also maintains a list of recently opened documents. This list is also located in the NTUSER hive. It can be found in the following location:

`NTUSER.DAT\Software\Microsoft\Office\VERSION`

The version number for each Microsoft Office release is different. An example registry key will look like this:

`NTUSER.DAT\Software\Microsoft\Office\15.0\Word`

Here, the 15.0 refers to Office 2013. A list of different Office releases and their version numbers can be found on [this link](https://docs.microsoft.com/en-us/deployoffice/install-different-office-visio-and-project-versions-on-the-same-computer#office-releases-and-their-version-number) .

Starting from Office 365, Microsoft now ties the location to the user's [live ID](https://www.microsoft.com/security/blog/2008/05/07/what-is-a-windows-live-id/) . In such a scenario, the recent files can be found at the following location. 

`NTUSER.DAT\Software\Microsoft\Office\VERSION\UserMRU\LiveID_####\FileMRU`

In such a scenario, the recent files can be found at the following location. This location also saves the complete path of the most recently used files.

#### ShellBags

When any user opens a folder, it opens in a specific layout. Users can change this layout according to their preferences. These layouts can be different for different folders. This information about the Windows _'shell'_  is stored and can identify the Most Recently Used files and folders. Since this setting is different for each user, it is located in the user hives. We can find this information on the following locations:

`USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\Bags`

`USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\BagMRU`

`NTUSER.DAT\Software\Microsoft\Windows\Shell\BagMRU`

`NTUSER.DAT\Software\Microsoft\Windows\Shell\Bags`

Registry Explorer doesn't give us much information about ShellBags. However, another tool from Eric Zimmerman's tools called the ShellBag Explorer shows us the information in an easy-to-use format. We just have to point to the hive file we have extracted, and it parses the data and shows us the results. An example is shown below. Take a look and answer Question # 2.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/666bd5bd3db41b4b6e3f09311f25666a.png)

#### Open/Save and LastVisited Dialog MRUs

When we open or save a file, a dialog box appears asking us where to save or open that file from. It might be noticed that once we open/save a file at a specific location, Windows remembers that location. This implies that we can find out recently used files if we get our hands on this information. We can do so by examining the following registry keys

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDlMRU`

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRU`

This is how Registry Explorer shows this registry key. Take a look to answer Question # 3 and 4.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/e996b8939895b4b5e55e780baa4335e9.png)

#### Windows Explorer Address/Search Bars

Another way to identify a user's recent activity is by looking at the paths typed in the Windows Explorer address bar or searches performed using the following registry keys, respectively.

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery`

Here is how the TypedPaths key looks like in Registry Explorer:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/782204163443e8f21ddd14297ba756dd.png)

#### Questions

![[Pasted image 20250728232132.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 8. Evidence of Execution

#### UserAssist

Windows keeps track of applications launched by the user using Windows Explorer for statistical purposes in the User Assist registry keys. These keys contain information about the programs launched, the time of their launch, and the number of times they were executed. However, programs that were run using the command line can't be found in the User Assist keys. The User Assist key is present in the NTUSER hive, mapped to each user's GUID. We can find it at the following location:

`NTUSER.DAT\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\{GUID}\Count`

Take a look at the below screenshot from Registry Explorer and answer Question #1.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/9bd8461865865ac3ff774c8a88d1afd5.png)

#### ShimCache

ShimCache is a mechanism used to keep track of application compatibility with the OS and tracks all applications launched on the machine. Its main purpose in Windows is to ensure backward compatibility of applications. It is also called Application Compatibility Cache (AppCompatCache). It is located in the following location in the SYSTEM hive:

`SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache`

ShimCache stores file name, file size, and last modified time of the executables.

Our goto tool, the Registry Explorer, doesn't parse ShimCache data in a human-readable format, so we go to another tool called AppCompatCache Parser, also a part of Eric Zimmerman's tools. It takes the SYSTEM hive as input, parses the data, and outputs a CSV file that looks like this:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/aad7dc918dbf3b1ab207dd71d03e8c0c.png)

We can use the following command to run the AppCompatCache Parser Utility:

`AppCompatCacheParser.exe --csv <path to save output> -f <path to SYSTEM hive for data parsing> -c <control set to parse>`

The output can be viewed using EZviewer, another one of Eric Zimmerman's tools.

#### AmCache

The AmCache hive is an artifact related to ShimCache. This performs a similar function to ShimCache, and stores additional data related to program executions. This data includes execution path, installation, execution and deletion times, and SHA1 hashes of the executed programs. This hive is located in the file system at:

`C:\Windows\appcompat\Programs\Amcache.hve`

Information about the last executed programs can be found at the following location in the hive:

`Amcache.hve\Root\File\{Volume GUID}\`

This is how Registry Explorer parses the AmCache hive:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/a569dfdf155c1a26fe3a693c388a44c7.png)

#### BAM/DAM

Background Activity Monitor or BAM keeps a tab on the activity of background applications. Similar Desktop Activity Moderator or DAM is a part of Microsoft Windows that optimizes the power consumption of the device. Both of these are a part of the Modern Standby system in Microsoft Windows.

In the Windows registry, the following locations contain information related to BAM and DAM. This location contains information about last run programs, their full paths, and last execution time.

`SYSTEM\CurrentControlSet\Services\bam\UserSettings\{SID}`

`SYSTEM\CurrentControlSet\Services\dam\UserSettings\{SID}`

Below you can see how Registry Explorer parses data from BAM:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/8a672c6580ab63d757ee5c08c09c924a.png)

#### Questions

![[Pasted image 20250728232851.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 9. External Devices/USB device forensics

When performing forensics on a machine, often the need arises to identify if any USB or removable drives were attached to the machine. If so, any information related to those devices is important for a forensic investigator. In this task, we will go through the different ways to find information on connected devices and the drives on a system using the registry.

#### Device identification

The following locations keep track of USB keys plugged into a system. These locations store the vendor id, product id, and version of the USB device plugged in and can be used to identify unique devices. These locations also store the time the devices were plugged into the system.

`SYSTEM\CurrentControlSet\Enum\USBSTOR`

`SYSTEM\CurrentControlSet\Enum\USB`

Registry Explorer shows this information in a nice and easy-to-understand way. Take a look at this and answer Questions # 1 and 2.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/03c87eaaf8458db97ffbddd30a6463e8.png)

#### First/Last Times

Similarly, the following registry key tracks the first time the device was connected, the last time it was connected and the last time the device was removed from the system.

`SYSTEM\CurrentControlSet\Enum\USBSTOR\Ven_Prod_Version\USBSerial#\Properties\{83da6326-97a6-4088-9453-a19231573b29}\####`

In this key, the #### sign can be replaced by the following digits to get the required information:

|   |   |
|---|---|
|**Value**|**Information**|
|0064|First Connection time|
|0066|Last Connection time|
|0067|Last removal time|

Although we can check this value manually, as we have seen above, Registry Explorer already parses this data and shows us if we select the USBSTOR key.

#### USB device Volume Name

The device name of the connected drive can be found at the following location:

`SOFTWARE\Microsoft\Windows Portable Devices\Devices`

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/6c9f71cdf4c71afdc19fc8c254a6a3cc.png) We can compare the GUID we see here in this registry key and compare it with the Disk ID we see on keys mentioned in device identification to correlate the names with unique devices. Take a look at these two screenshots and answer Question # 3.

Combining all of this information, we can create a fair picture of any USB devices that were connected to the machine we're investigating.

#### Questions

![[Pasted image 20250728234818.png]]
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 10. Hands-on Challenge

So, now that we have learned something, let's put it into practice. 

Launch the VM attached with the task. A Windows VM should show up in the right half of your browser window. Please allow a few minutes for the machine to boot. If you don’t see a Desktop, click the Show Split Screen button at the top right of the page.

#### The Setup:

If preferred, use the following credentials to log into the machine:

**Username:** THM-4n6

**Password:** 123

Once we log in, we will see two folders on the Desktop named `triage` and `EZtools`. 

The `triage` folder contains a triage collection collected through KAPE, which has the same directory structure as the parent. This is where our artifacts will be located. 

The `EZtools` folder contains Eric Zimmerman's tools, which we will be using to perform our analysis. You will also find RegistryExplorer, EZViewer, and AppCompatCacheParser.exe in the same folder.

**Note:** Although the Autopsy tool on the Desktop can be used to solve this case, it is recommended that you use the `EZtools`, as demonstrated in this room.

#### The Challenge:

﻿Now that we know where the required toolset is, we can start our investigation. We will have to use our knowledge to identify where the different files for the relevant registry hives are located and load them into the tools of our choice. Let's answer the questions below using our knowledge of registry forensics.

##### Scenario:

One of the Desktops in the research lab at Organization X is suspected to have been accessed by someone unauthorized. Although they generally have only one user account per Desktop, there were multiple user accounts observed on this system. It is also suspected that the system was connected to some network drive, and a USB device was connected to the system. The triage data from the system was collected and placed on the attached VM. Can you help Organization X with finding answers to the below questions?

**Note:** When loading registry hives in RegistryExplorer, it will caution us that the hives are dirty. This is nothing to be afraid of. We just need to remember the little lesson about transaction logs and point RegistryExplorer to the .LOG1 and .LOG2 files with the same filename as the registry hive. It will automatically integrate the transaction logs and create a 'clean' hive. Once we tell RegistryExplorer where to save the clean hive, we can use that for our analysis and we won't need to load the dirty hives anymore. RegistryExplorer will guide you through this process.

#### Questions

![[Pasted image 20250729102658.png]]
![[Pasted image 20250729102923.png]]

![[Pasted image 20250729103228.png]]
![[Pasted image 20250729103549.png]]

![[Pasted image 20250729103919.png]]

<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

### 11. Conclusion

---

## References

https://tryhackme.com/room/windowsforensics1