# Introduction to Windows
The Windows operating system, dominant in both home and corporate networks, has faced persistent targeting by hackers and malware creators since its inception in 1985. 
Windows XP, a popular version, was succeeded by Windows Vista, which faced widespread criticism and was quickly phased out. 
Windows 7 became the preferred choice until Windows 10's arrival, currently the standard for desktop computers, offered in Home and Pro versions. Windows Server 2019 serves as the current version for servers. 
Despite criticisms, Microsoft continually improves Windows' usability and security with each iteration. As of October 2021, Windows 11 has become the latest operating system for end-users.

# The File System
Modern versions of Windows utilize the **NTFS** (New Technology File System), replacing older systems like **FAT16/FAT32** (File Allocation Table) and **HPFS** (File Allocation Table)

While FAT partitions remain common in USB devices and MicroSD cards, NTFS is standard for Windows computers and servers.
NTFS offers journaling, automatically repairing disk data in case of failure, a feature absent in FAT.
It addresses limitations of previous systems, supporting larger files, setting specific permissions, compression, and encryption (via Encryption File System or EFS).

You can read Microsoft's official documentation on FAT, HPFS, and NTFS [here](https://docs.microsoft.com/en-us/troubleshoot/windows-client/backup-and-storage/fat-hpfs-and-ntfs-file-systems).

On NTFS volumes, you can set permissions such as:
- **Full control**
- **Modify**
- **Read & Execute**
- **List folder contents**
- **Read**
- **Write**

**NTFS permissions** for Special Permissions can be better understood through [Microsoft documentation](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc754344(v=ws.11)).

Another feature of NTFS is **Alternate Data Streams (ADS)**, a file attribute specific to Windows NTFS.

**ADS** allows files to contain multiple streams of data, including a default data stream (`$DATA`). While Windows Explorer doesn't display **ADS** by default, **PowerShell** enables viewing **ADS** for files.

**Malware writers** have exploited **ADS** to hide data, but it also has benign uses, such as adding identifiers to downloaded files to indicate their source.

## Windows/System32
The **Windows folder** (C:\Windows) traditionally houses the **Windows operating system**.

It can exist on any drive and in any folder, not limited to the C drive.

**Environment variables**, particularly **system environment variables**, play a crucial role. The system environment variable for the Windows directory is `%windir%`.

According to **Microsoft**, "Environment variables store information about the operating system environment," including the **operating system path** and **temporary folder locations**.

The **'Windows' folder** contains numerous subfolders.
One of those subfolders is **System32** it holds critical files for the OS.

# User Accounts, Profiles and Permissions
User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**. 

The user account type will determine what actions the user can perform on that specific Windows system. 

- An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
- A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

To manage Users and Groups: `lusrmgr.msc` 
## User Account Control (UAC)
The **majority of home users** are logged into their **Windows systems** as **local administrators**, granting them the ability to make changes to the system.

Running with **elevated privileges** increases the risk of system compromise, making it easier for **malware** to infect the system. Malware would run in the context of the logged-in user.

**User Account Control (UAC)** was introduced by **Microsoft** to protect local users with such privileges, starting with **Windows Vista**.

When an operation requiring higher-level privileges needs to execute, **UAC** prompts the user to confirm if they permit the operation to run.

**UAC** does not apply by default for the **built-in local administrator account**.

In the **Security tab** of the **program properties**, users/groups and their permissions are listed, with the standard user typically not included.

# System Configuration
The utility for this `MSConfig` is for advanced troubleshooting, and its main purpose is to help diagnose start-up issues. (It requires Administrator rights)

- **General** tab, we can select what devices and services for Windows to load upon boot.
The options are: **Normal**, **Diagnostic**, or **Selective**. 
-  **Boot** tab, we can define various boot options for the Operating System.
- **Services** tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.  
- **Startup** tab, you won't see anything interesting in the attached VM.

Microsoft advises using **Task Manager (**`taskmgr`**)** to manage (enable/disable) start-up items. The System Configuration utility is **NOT** a start-up management program.