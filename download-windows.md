Skip to main contentSkip to Ask Learn chat experience
Microsoft Ignite
November 17–20, 2026

Learn
Sign in
Windows Developer Tools
Search
Find by title
WSL Documentation
Install WSL
Manual install steps for older versions
Install on Windows Server
Frequently Asked Questions
Troubleshooting
LearnWindowsWSL
How to install Linux on Windows with WSL

Summarize this article for me
In this article
Prerequisites
Install WSL command
Change the default Linux distribution installed
Set up your Linux user info
Show 8 more
Developers can access the power of both Windows and Linux at the same time on a Windows machine. The Windows Subsystem for Linux (WSL) lets developers install a Linux distribution (such as Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc) and use Linux applications, utilities, and Bash command-line tools directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

Prerequisites
You must be running Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11 to use the commands below. If you are on earlier versions please see the manual install page.

Install WSL command
You can now install everything you need to run WSL with a single command. Open PowerShell in administrator mode by right-clicking and selecting "Run as administrator", enter the wsl --install command, then restart your machine.

PowerShell
wsl --install
This command will enable the features necessary to run WSL and install the Ubuntu distribution of Linux. (This default distribution can be changed).

If you're running an older build, or just prefer not to use the install command and would like step-by-step directions, see WSL manual installation steps for older versions.

The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for files to de-compress and be stored on your machine. All future launches should take less than a second.

 Note

The above command only works if WSL is not installed at all. If you run wsl --install and see the WSL help text, please try running wsl --list --online to see a list of available distros and run wsl --install -d <DistroName> to install a distro. If the install process hangs at 0.0%, run wsl --install --web-download -d <DistroName> to first download the distribution prior to installing. To uninstall WSL, see Uninstall legacy version of WSL or unregister or uninstall a Linux distribution.

Change the default Linux distribution installed
By default, the installed Linux distribution will be Ubuntu. This can be changed using the -d flag.

To change the distribution installed, enter:

PowerShell
wsl.exe --install -d [Distro]
Replace [Distro] with the name of the distribution you would like to install.

To see a list of available Linux distributions available for download through the online store, enter:

PowerShell
wsl.exe --list --online
If you run into an issue during the install process, check the installation section of the troubleshooting guide.

To install a Linux distribution that is not listed as available, you can import any Linux distribution using a TAR file. Or in some cases you can install using an .appx file. You can also create your own custom Linux distribution to use with WSL.

Set up your Linux user info
Once you have installed WSL, you will need to create a user account and password for your newly installed Linux distribution. See the Best practices for setting up a WSL development environment guide to learn more.

Set up and best practices
We recommend following our Best practices for setting up a WSL development environment guide for a step-by-step walk-through of how to set up a user name and password for your installed Linux distribution(s), using basic WSL commands, installing and customizing Windows Terminal, set up for Git version control, code editing and debugging using the VS Code remote server, good practices for file storage, setting up a database, mounting an external drive, setting up GPU acceleration, and more.

Check which version of WSL you are running
You can list your installed Linux distributions and check the version of WSL each is set to by entering the command:

PowerShell
wsl.exe --list --verbose
To set the default version to WSL 1 or WSL 2 when a new Linux distribution is installed, use the command:

PowerShell
wsl.exe --set-default-version <1|2>
To set the default Linux distribution used with the wsl command, enter:

PowerShell
wsl.exe --set-default <Distro>
Replacing <Distro> with the name of the Linux distribution you would like to use. For example, from PowerShell, enter: wsl -s Debian to set the default distribution to Debian. Now running wsl npm init from Powershell will run the npm init command in Debian.

To run a specific wsl distribution from within PowerShell without changing your default distribution, use the command:

PowerShell
wsl.exe --distribution <DistroName>
Replacing <DistroName> with the name of the distribution you want to use.

Learn more in the guide to Basic commands for WSL.

Upgrade version from WSL 1 to WSL 2
New Linux installations, installed using the wsl --install command, will be set to WSL 2 by default.

To see whether your Linux distribution is set to WSL 1 or WSL 2, use the command: wsl -l -v. Upgrading from WSL 1 to WSL 2 or downgrading from WSL 2 to WSL 1 can be done using the following command:

PowerShell
wsl.exe --set-version <Distro> <1|2>
Replacing <Distro> with the name of the Linux distribution that you want to update. For example, wsl --set-version Ubuntu 2 will set your Ubuntu distribution to use WSL 2.

If you manually installed WSL prior to the wsl --install command being available, you may also need to enable the virtual machine optional component used by WSL 2 and install the kernel package if you haven't already done so.

To learn more, see the Command reference for WSL for a list of WSL commands, Comparing WSL 1 and WSL 2 for guidance on which to use for your work scenario, or Best practices for setting up a WSL development environment for general guidance on setting up a good development workflow with WSL.

Ways to run multiple Linux distributions with WSL
WSL supports running as many different Linux distributions as you would like to install. This can include choosing distributions from the Microsoft Store, importing a custom distribution, or building your own custom distribution.

There are several ways to run your Linux distributions once installed:

From Windows Terminal (Recommended) Using Windows Terminal supports as many command lines as you would like to install and enables you to open them in multiple tabs or window panes and quickly switch between multiple Linux distributions or other command lines (PowerShell, Command Prompt, Azure CLI, etc). You can fully customize your terminal with unique color schemes, font styles, sizes, background images, and custom keyboard shortcuts. Learn more.
You can directly open your Linux distribution by visiting the Windows Start menu and typing the name of your installed distributions. For example: "Ubuntu". This will open Ubuntu in its own console window.
From PowerShell, you can enter the name of your installed distribution. For example: ubuntu
From PowerShell, you can open your default Linux distribution inside your current command line, by entering: wsl.exe.
From PowerShell, you can use your default Linux distribution inside your current command line, without entering a new one, by entering:wsl [command]. Replacing [command] with a WSL command, such as: wsl -l -v to list installed distributions or wsl pwd to see where the current directory path is mounted in wsl. From PowerShell, the command Get-Date will provide the date from the Windows file system and wsl date will provide the date from the Linux file system.
The method you select should depend on what you're doing. If you've opened a WSL command line within a PowerShell window and want to exit, enter the command: exit.

Want to try the latest WSL preview features?
Try the most recent features or updates to WSL by joining the Windows Insiders Program. Once you have joined Windows Insiders, you can choose the channel you would like to receive preview builds from inside the Windows settings menu to automatically receive any WSL updates or preview features associated with that build. You can choose from:

Canary Channel:
Ideal for highly technical users.
Preview the latest platform changes early in the development cycle.
These builds can be unstable and are released with limited to no documentation.
Dev Channel:
Ideal for enthusiasts.
Access the latest Windows 11 preview builds as we incubate new ideas and develop long lead features.
There will be some rough edges and low stability.
Beta Channel:
Ideal for early adopters.
Preview and provide feedback on pre-release features for Windows 11 in a stable environment.
Release Preview Channel:
Ideal if you want to preview fixes and certain key features, plus get optional access to the next version of Windows before it’s generally available to the world.
This channel is also recommended for commercial users.
If you prefer not switching your Windows installation to a preview channel, you can still test the latest preview of WSL by issuing the command:

PowerShell
wsl.exe --update --pre-release
For more information check the WSL Releases page on GitHub.

Next Steps
Let's explore the basic commands of WSL next.


Offline install
To install WSL offline, you need to do these steps:

Download and install latest WSL MSI package from the GitHub releases page
Open a PowerShell window with admin privileges and run dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart to enable the Virtual Machine Platform optional component. You will likely need to restart your computer for this to take effect.
Install a distribution via a .wsl file. You can find URLs to download these files at DistributionInfo.json for your chosen distro.
Additional resources
Windows Command Line Blog: Install WSL with a single command now available in Windows 10 version 2004 and higher
 Collaborate with us on GitHub
The source for this content can be found on GitHub, where you can also create and review issues and pull requests. For more information, see our contributor guide.

Windows Subsystem for Linux feedback

Windows Subsystem for Linux is an open source project. Select a link to provide feedback:

 Open a documentation issue
 Provide product feedback
Feedback
Was this page helpful?

Additional resources
Documentation

Manual installation steps for older versions of WSL

Step by step instructions to manually install WSL on older versions of Windows, rather than using the wsl install command.

Basic commands for WSL

Reference for the basic commands included with Windows Subsystem for Linux (WSL).

Comparing WSL Versions

WSL 2 provides the benefits of WSL 1, but uses an actual Linux kernel, rather than a translation layer like WSL 1, resulting in faster performance.

Show 3 more
Training

Module

Developing in the Windows Subsystem for Linux with Visual Studio Code - Training

In this module, you learn how to use the Windows Subsystem for Linux (WSL) with Visual Studio Code (VS Code). We explore the installation process and the basics of using WSL. Additionally, we install and utilize the Visual Studio Code WSL extension. Finally, we demonstrate how to debug and run Python code in VS Code within our WSL environment.

Certification

Microsoft Certified: Windows Server Hybrid Administrator Associate - Certifications

As a Windows Server hybrid administrator, you integrate Windows Server environments with Azure services and manage Windows Server in on-premises networks.

Last updated on 08/06/2025
AI Disclaimer
Previous Versions
Blog
Contribute
Privacy
Consumer Health Privacy
Terms of Use
Trademarks
© Microsoft 2026



------


Skip to main contentSkip to Ask Learn chat experience
Microsoft Ignite
November 17–20, 2026

Learn
Sign in
Windows Developer Tools
Search
Find by title
WSL Documentation
Import any Linux distribution
Build a custom distribution
Mount a disk in WSL 2
Connect USB devices
Adjust case sensitivity
Manage available disk space
Create WSL plugins
Frequently Asked Questions
Troubleshooting
LearnWindowsWSL
Connect USB devices

Summarize this article for me
In this article
Prerequisites
Install the USBIPD-WIN project
Attach a USB device
This guide will walk through the steps necessary to connect a USB device to a Linux distribution running on WSL 2 using the USB/IP open-source project, usbipd-win.

Setting up the USB/IP project on your Windows machine will enable common developer USB scenarios like flashing an Arduino or accessing a smartcard reader.

Prerequisites
Running Windows 11 (Build 22000 or later). (Windows 10 support is possible, see note below).
A machine with an x64 or ARM64 processor is required. (x86 is currently not supported with usbipd-win).
WSL is installed and set up with the latest version.
Linux distribution installed and set to WSL 2.
 Note

To check your Windows version and build number, select Windows logo key + R, type winver, select OK. You can update to the latest Windows version by selecting Start > Settings > Windows Update > Check for updates. To check your Linux kernel version, open your Linux distribution and enter the command: uname -a. To manually update to the latest kernel, open PowerShell and enter the command: wsl --update.

 Important

WSL now supports both Windows 10 and Windows 11 via the Microsoft Store, meaning that Windows 10 users now have access to the latest kernel versions without needing to compile from source. See WSL in the Microsoft Store is now generally available on Windows 10 and 11 for info on how to update to the Store-supported version of WSL. If you are unable to update to the Store-supported version of WSL and automatically receive kernel updates, see the USBIPD-WIN project repo for instructions on connecting USB devices to a Linux distribution running on WSL 2 by building your own USBIP enabled WSL 2 kernel.

Install the USBIPD-WIN project
Support for connecting USB devices is not natively available in WSL, so you will need to install the open-source usbipd-win project.

Kernel requirements
To use USBIPD with Windows Subsystem for Linux (WSL), you need to have a Linux kernel version of 5.10.60.1 or higher. If the installed kernel version is older than 5.10.60.1, then it can be updated by first shutting down any running instances of WSL with wsl --shutdown, then running the command: wsl --update.

Install USBIPD on WSL
Go to the latest release page for the usbipd-win project.
Select the .msi file, which will download the installer. (You may get a warning asking you to confirm that you trust this download).
Run the downloaded usbipd-win_x.msi installer file.
 Note

Alternatively, you can also install the usbipd-win project using Windows Package Manager (winget). If you have already installed winget, just use the command: winget install --interactive --exact dorssel.usbipd-win to install usbipd-win. If you leave out --interactive, winget may immediately restart your computer if that is required to install the drivers.

This will install:

A service called usbipd (display name: USBIP Device Host). You can check the status of this service using the Services app from Windows.
A command line tool usbipd. The location of this tool will be added to the PATH environment variable.
A firewall rule called usbipd to allow all local subnets to connect to the service. You can modify this firewall rule to fine tune access control.
Attach a USB device
Before attaching your USB device, ensure that a WSL command line is open. This will keep the WSL 2 lightweight VM active.

 Note

This doc assumes that you have usbipd-win 5.0.0 or higher installed

List all of the USB devices connected to Windows by opening PowerShell in administrator mode and entering the following command. Once the devices are listed, select and copy the bus ID of the device you’d like to attach to WSL.

PowerShell
usbipd list
Before attaching the USB device, the command usbipd bind must be used to share the device, allowing it to be attached to WSL. This requires administrator privileges. Select the bus ID of the device you would like to use in WSL and run the following command. After running the command, verify that the device is shared using the command usbipd list again.

PowerShell
usbipd bind --busid 4-4
To attach the USB device, run the following command. (You no longer need to use an elevated administrator prompt.) Ensure that a WSL command prompt is open in order to keep the WSL 2 lightweight VM active. Note that as long as the USB device is attached to WSL, it cannot be used by Windows. Once attached to WSL, the USB device can be used by any distribution running as WSL 2. Verify that the device is attached using usbipd list. From the WSL prompt, run lsusb to verify that the USB device is listed and can be interacted with using Linux tools.

PowerShell
usbipd attach --wsl --busid <busid>
Open Ubuntu (or your preferred WSL command line) and list the attached USB devices using the command:

Bash
lsusb
You should see the device you just attached and be able to interact with it using normal Linux tools. Depending on your application, you may need to configure udev rules to allow non-root users to access the device.

Once you are done using the device in WSL, you can either physically disconnect the USB device or run this command from PowerShell:

PowerShell
usbipd detach --busid <busid>
To learn more about how this works, see the Windows Command Line Blog and the usbipd-win repo on GitHub.

For a video demonstration, see WSL 2: Connect USB devices (Tabs vs Spaces show).

 Collaborate with us on GitHub
The source for this content can be found on GitHub, where you can also create and review issues and pull requests. For more information, see our contributor guide.

Windows Subsystem for Linux feedback

Windows Subsystem for Linux is an open source project. Select a link to provide feedback:

 Open a documentation issue
 Provide product feedback
Feedback
Was this page helpful?

Last updated on 07/02/2024
AI Disclaimer
Previous Versions
Blog
Contribute
Privacy
Consumer Health Privacy
Terms of Use
Trademarks
© Microsoft 2026
