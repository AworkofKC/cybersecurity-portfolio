
# Journal Index
- [Introduction](#introduction)
- [Installing Virtual Box (VM)](#installing-virtual-box-vm)
- [Downloading Security Onion- ISO Image](#downloading-security-onion---iso-image)
- [Download Verification](#download-verification)
- [Security Onion Installation](#security-onion-installation)
- [Problems & How I tackled them](#problems--how-i-tackled-them) *(during SO installation)*
- [Reflection and Next steps](#reflection-and-next-steps)


## Introduction
I’m an aspiring Professional SOC Analyst and Incident Responder, currently deep in my learning journey. I started this journal to document my self‑learning and hands‑on experiments, as well as the lessons I pick up along the way.

This is my way of sharing what I’m doing while chasing my dream career. I'm a researcher at heart and I love figuring things out. I’m no genius, and right now I don’t have all the answers, but I’m committed to the process or trial and error. Hang in there with me while I figure it out.

## Trying something crazy

With more sites locking content behind paywalls, hands‑on learning has become a bit hard and I often end up with gaps in my knowledge. So, after some research, I stumbled onto a free, open‑source platform called **Security Onion**.

I decided to give it a try, my goal? To move and think like an SOC analyst.  

Right now, I’m downloading Security Onion in a VirtualBox setup so I can explore what it feels like to monitor, investigate, and respond to incidents—from the first alert to the final report.  
To support my learning, I’ve been leveraging:

- 🔍 **Research tools** like Google and GitHub communities
- 🤖 **AI tools** including ChatGPT (Reg) and Copilot
- 📚 **Books** like MITRE’s 11 Strategies of a World-Class SOC

These resources help me simplify complex concepts and build a clearer understanding of security tools, workflows, and threat defense strategies..


<br>

## Installing Virtual Box (VM) 
Date: 08-22-2025

**Event**: I downloaded the Oracle VirtualBox-*Version 7.2.0*

*Reasoning*:  
I wanted a way to keep my host-device protected while attempting to download and test Security Onion, so a virtual machine seems like the safest route.

*Process:*
- Went to the official VirtualBox site
- Downloaded the .exe for Windows *(version 7.2.0)*
- Ran the installer and stuck with the defaults

*Learning Opportunity:*  
The download was straightforward. I stuck with the default settings for now I didn’t touch anything advanced yet. I’ll look into networking and VM settings once I know what Security Onion actually needs.

*Source*: 
[VirtualBox Official Downloads Page](https://www.virtualbox.org/wiki/Downloads)



## Downloading Security Onion - ISO Image
Date: 08-22-2025


**Event**: Downloaded the 2.4.170-20250812 ISO image file for Security Onion. First install attempt.

*Reasoning:*
- I found Security Onion during regular online research. I was looking for realistic, hands-on ways to practice SOC (Security Operations Center) workflows.I learned it’s an open-source platform used for threat hunting, security monitoring, and log management. I decided to make this my main project while working toward an SOC analyst position.


*Process:*
- In my initial setup, I added the VM name and selected the ISO image.
- VirtualBox autofilled the OS distribution as Oracle Linux *(64-bit)*
- I proceeded to start the VM.
-Received an error: “You don’t have enough space allocated on your disk to download the program.”


*Learning Opportunity:*
- I believed the space required for Security Onion was covered by my host machine’s configuration. Turns out, I needed to configure the VirtualBox machine itself.
- Tried to adjust settings to fix the storage allocation, but I am unable to change these settings post-setup.
- I’ve removed the partial install and will do a clean reinstallation with proper disk allocation.


*Sources*:  
[Download & Verify ISO – GitHub](https://github.com/Security-Onion-Solutions/securityonion/blob/2.4/main/DOWNLOAD_AND_VERIFY_ISO.md)  
[First-Time Users – Security Onion Docs](https://docs.securityonion.net/en/2.4/first-time-users.html)





## Download Verification
Date: 08-25-2025

**Event**: I Verified the Signature Keys, and SHA256 Hash of the Security Onion.iso file.

*Reasoning*:  
 Due to the substantial file size and the potential for multiple re-installations, I wanted to make sure that I am confirming the integrity of the iso file I download.

*Process:*  
- I researched way to verify file certificate; I found and downloaded "Gpg4win 4.4.1 Or Kleopatra" (Released: 2025-05-21), which is a Windows based certification manager and GUI used for verifying and storing certificates and keys.
-I downloaded the iso.sig file, and I saved the public key block as an .asc file which allowed me to upload it in the GPG software.
- I was able to use the "Decrypt/Verify" Section to upload the signature file and Key. I received a message that reflect "good signature"
-I verified the hash using `certutil -hashfile` along with the iso file path to verify the SHA256 hash provided. A matching Hash value was confirmed, which is great.

*Learning Opportunity*:
- Downloading the Gpg software was fairly simple to maneuver, the GUI made it easy to locate the buttons or sections needed to upload the files and verify keys.
- The Security Onion signing key was web-based, so I was initially unable to easily verify it. I had to copy and paste it into a notepad or .txt document; I then changed the file type to .asc for an easier import.
- When checking the file hash, I wanted to confirm it matched without reading every character line‑by‑line. For verification, I used AI (ChatGPT) along with my cheat sheet to extend the command with `>nul, | findstr /i, &&, ||`, and `echo`, This allowed me to print a Yes or No based on the result.

*Source*: 
[GPG(Kleopatra) for Windows](https://www.virtualbox.org/wiki/Downloads)  
[Security Onion/Download and verify](https://github.com/Security-Onion-Solutions/securityonion/blob/2.4/main/DOWNLOAD_AND_VERIFY_ISO.md)


## Baseline Configurations & Environment


##
**Date:** 08/25/2025

**Event**: Documented list of baseline configurations.

*Reasoning*:  
Most of the problems I encountered happened during my first install attempt. I assumed the setup would be straightforward, like any other download, but I ran into multiple issues that made me step back and review Security Onion’s VirtualBox instructions more carefully. That process helped me realize I had missed several key baseline configurations. I’m noting them here before starting a clean reinstallation to avoid repeating the same mistakes.

*Environment/Baseline*:  
- **Host OS:** Windows 11
- **Virtualization:** VirtualBox
- **OS Version:** Oracle Linux
- **SO node type:** Import
- **CPU:** 2 minimum
- **RAM:** 4 GB or 4096 Base Memory *(There is no specific "RAM" section to edit)*
- **Storage:** 200GB Minimum *(due to computer specs, SO only supports standard Intel or AMD 64-bit processors)*
- **Adapter:** 1 Adapter: NAT


Source:  
[Installing Security Onion on Virtual Box](https://docs.securityonion.net/en/2.4/virtualbox.html)  
[Security Onion Documentation](https://docs.securityonion.net/en/2.4/index.html)


##
**Updated:** 08/31/2025

*Reasoning*  
Although there are recommended configurations when using the Security Onion ISO in VirtualBox, I realized that some settings may need a few tweaks to work properly on my specific device. A few elements required updates, and I wanted to make a note of them

*Environment/Baseline*:  
- **Host OS:** Windows 11
- **Virtualization:** VirtualBox
- **OS Version:** Oracle Linux
- **SO node type:** Import
- **CPU:** 2 - Enable UEFI
- **RAM:** 4 GB or 4096 Base Memory *(There is no specific "RAM" section to edit)*
- **Processing Cap/Execution Cap:** 85%
- **Storage:** At least 100 GB
- **Apdater:** 1 Adapter: NAT
- 

##

**Updated:** 09/06/2025

*Reasoning*  
After what I thought was a clean install, I still faced a few challenges that required heavy research. I was able to fully install Security Onion and reach a completed stage, but some of the configuration choices still caused additional issues. I am still unable to access the SOC UI through my web browser. This entry includes the additional install components and settings used now that I have made it this far.


*Environment/Baseline*:  
- **Host OS:** Windows 11
- **Virtualization:** VirtualBox
- **OS Version:** Oracle Linux
- **SO node type:** Import
- **CPU:** 4 - Enable UEFI
- **RAM:** 4 GB or 4096 Base Memory *(There is no specific "RAM" section to edit)*
- **Processing Cap/Execution Cap:** 85%
- **Storage:** At least 100 GB
- **Adapter:** 2 Adapters - 1: Host-Only, 2: NAT.
- 

## 

## Security Onion Installation
Date: 08/29/2025

**Event:** Full-Clean re-installation of Security Onion

*Reasoning:*   
After multiple failed attempts and lessons learned from disk space issues, power interruptions, and configuration oversights, I decided it was time for a clean, intentional reinstallation of Security Onion. I wanted to start fresh with updated baseline configs, verified downloads, and a clearer understanding of what each step actually does. These are the steps that provided me with the best overall results.

*Process:*  
- Verified ISO signature using Kleopatra
- Verified SHA256 Hash via host command line
- Created "New" VM, Uploaded so.iso file *(Oracle Linux was selected automatically)*
- Updated hard disk sepcs to 200GB disk size
- Went to system settings to update processor the Base Memory and enable recording. *(using baseline min. configs, 2 CPU, 4096 BM)*



##

## Problems & How I Tackled Them

This section documents the issues I ran into during my Security Onion install and lab setup. Some were small, some were frustrating, but each one taught me something. I’m logging them here with the cause, impact, resolution, and what I learned — not just for future reference, but to capture the actual process of figuring things out.  

*Note: Most if not all issues led to removing the VM and doing a clean reinstallation. Additionally, I’ve also included minor problems, since small fixes can lead to bigger lessons.*

**Lab Context:** Security Onion 2.4.x on VirtualBox  
Date: August 2025  



🔗**Index**
- [VM Name Conflict After Manual Deletion](#vm-name-conflict-after-manual-deletion)
- [CPU stuck for 6343 seconds](#cpu-stuck-for-6343-seconds)
- [Disk Space Requirement - 99GB Minimum](#disk-space-requirement---99gb-minimum)
- [Salt State Failure During Setup](#salt-state-failure-during-setup)
- [Forgotten Password](#forgotten-password)
- [Resource Exhaustion](#resource-exaustion)
- [Host Device Malfunction](#host-device-malfunction)
- [Kernal BUG](kernal-bug)
- [SOC GUI unreachable after install](#soc-gui-unreachable-after-install)
- [Security Onion Management IP Detection Failure](#security-onion-management-ip-detection-failure)
- [SO Management IP Detection Failure - Update](#so-management-ip-detection-failure---update)




## VM Name Conflict After Manual Deletion. 
Date: 08/22/2025

🔴 **Cause:**
- Although I selected the "remove files" when deleting the virtual machine, some associated files still remain on the host.  

🟡 **Impact:**
- The attempt to create a new VM with the same name failed.
- VirtualBox flagged name as already in use, despite no visible VM in GUI.  

🟢 **Resolution:**
- Opened VirtualBox → File → Tools → Virtual Media Manager and manually removed any orphaned disk entries.
- Verified no lingering .vbox or .vdi files in C:\drive
- Restarted VirtualBox and successfully created new VM with same name.

*Lesson Learned:*   
Deleting a VirtualBox VM doesn’t fully unregister it from the host machine. Always check for remaining VM config files or virtual hard disks before attempting to recreate a VM with the same name.



## CPU stuck for 6343 seconds 
Date: 08/22/2025

🔴*Cause:*   
- Host machine entered sleep mode during Security Onion install

🟡*Impact:* 
- VM froze, install may have stalled.
- Applied sudo reboot

🟢*Resolution:*
  - Disabled sleep mode on host-machine
  - Rebooted VM and verified service status

Lesson:  
Because Security Onions installation can and take anywhere from a few mins to even a couple of hours, it is important to ensure to update battery and screen saving preferences to prevent sleep mode interruptions.


## Disk Space Requirement - 99GB Minimum

Date: 08/22/2025

🔴 **Cause:**
 - VM disk size was set below SO 2.4’s minimum threshold.  

🟡**Impact:**  
- Installer halted; install could not proceed
- Misalignment between VM config and SO requirements

🟢 **Resolution:**  
- Increased VirtualBox disk size to 200GB 
- Re-ran installation

*Lesson:*  
Security Onion 2.4 enforces a 99GB minimum disk size. Always check version-specific requirements and allocate space accordingly, even in lab environments. Also, ensure a hard disk is selected during VM creation, as it’s required for installation to proceed. I missed this step during setup, which blocked the install.



## Salt State Failure During Setup
Date: 08/22/2025

🔴 **Cause:** 
- Stalled Installation
- Host lost power during setup

🟡**Impact:**
- Configuration services were not fully deployed
-	Logs showed partial state application

🟢 **Resolution:**
-	Used `so-status` to check the current status on salt-stack
- Ran `state.highstate` to reapply states
-	Rebooted VM and re-ran 

Lesson:
I leveraged Google and Co-pilot to help to better understand Salt state/SaltStack, which defines the desired state of a system and ensuring compliance across the infrastructure. Due to the sensitivity of ISO based installs, I realized it is better to do a clean reinstallation instead of attempting to make changes via the command line.

*Note:* Why I Chose Reinstall Over Recovery:
- Risk of partial or corrupted state  
- Uncertainty around what configurations were skipped  
- Clean install allows me to be more confident once completed.



## Forgotten Password
Date: 08/29/2025

🔴 **Cause:**  
- Misspelled password
- Possibly entered the wrong password

🟡 **Impact:**  
- Unable to proceed with setup or installation

🟢 **Resolution:**  
- Removed Security Onion from the VM
- Performed a clean reinstallation

📘 **Lesson Learned:**  
It’s important to safely record passwords or login credentials during the Security Onion install, there’s no “redo” or password reset option once it’s set.



## Resource Exhaustion

Date: 08/29/2025

🔴 *Cause:*  
- System Froze on Welcome installation screen due to high CPU utilization. 

🟡 *Impact:*  
- Unable to type "yes" to continue installation
- Cause blinking light on caps lock button signaling a hardware/driver-level fault.  

🟢 *Resolution:*  
- Powered off the VM
- Checked Host CPU usage *(Currently running ~85%)*
- Closed extra unessary tabs
- Reduced VM Processing Cap from 100% to 85%
- Restarted Security Onion installation

Lesson Learned:  
A blinking light reflected on the Caps Lock key can be an indicator of issues with hardware, such as motherboard, RAM, CPU or other driver concerns. In this case, a high CPU strain on the host system caused the VM to freeze. Applying a processing cap can stabilize performance by preventing the VM from overconsuming host resources.  



## Host Device Malfunction  

Date: 08/31/2025  

🔴 *Cause:*  
- USB/Bluetooth mouse became unresponsive after VM froze and host resource exhaustion.  
- Possible conflict with Bluetooth support services and input drivers.  

🟡 *Impact:*  
- Loss of mouse control and Bluetooth connections after host restart.  
- Required switching to keyboard-only navigation temporarily.  

🟢 *Resolution:*  
- Restarted host system.  
- Removed device from the system Device Manager.
- Halted and restarted Windows Bluetooth Support services.
- Reconnected and verified mouse functionality before re-launching VM.  

Lesson Learned:  
High CPU usage can lead to other conflicts such as malfunctions with host drivers (USB/Bluetooth).

## Kernel BUG  

Date:  
09/06/2025

🔴 *Cause:*  
- During VM boot, a kernel bug message appeared on-screen while looking at `ip addr` 
- Likely triggered by VM choking on limited resources while trying to boot and start services like salt-minion, nginx, elasticsearch, and others all at once


🟡 *Impact:*  
- No immediate crash or halt, the system continued booting 
- Received message stating `kernel: watchdog: BUG: soft lockup - CPU#0 stuck for 151s!`
- SOC services appeared to start normally  
- Unclear if bug affects performance or stability  

🟢 *Resolution:*  
- Captured screenshot for reference  
- Shutdown the VM and allocated 4 CPUs instead of 2.


Lesson Learned:  
Kernel bug messages may appear during VM boot without causing visible failure. Security Onion is heavy, and VirtualBox doesn’t always handle that load gracefully, especially during first boot. I will track this across installs to determine if it’s persistent or environment-specific.
  
## SOC GUI unreachable after install  

Date:  
09/06/2025 


🔴 *Cause:*  
- Security Onion was installed using NAT networking and an IP-based setup.
- Host machine could not reach `10.0.2.15` due to NAT isolation  

🟡 *Impact:*  
- SOC web interface was inaccessible from host browser  
- Redirects to `http://10.0.2.15` consistently failed with timeout.


🟢 *Resolution:*  
- Checked host device to ensure it was listening on forwarded port `8443`.
- Decided to wipe the VM and reinstall using Host-Only Adapter  
- Will assign IP from VM Host-Only IP address during setup  
- Will use NAT as an alternative if internet access is needed

Lesson Learned:  
Redirect behavior in Security Onion is tied directly to install IP and Adapter choices. NAT networking created unreachable redirections, and prevented access to the Security Onion web interface. Host-Only Adapter provides a cleaner, safer, and more predictable lab setup. Next time, I’ll choose a network setup that lets my host reach the SOC UI directly without needing port forwarding or other configurations. I’ll avoid IPs that the host can’t access and test connectivity before finishing the install.


## Security Onion Management IP Detection Failure

Date:
09/07/2025

🔴 Cause:

I changed the VM’s network settings after the installer had already partially configured the system. This prevented the installer from detecting the management IP.

🟡 Impact:

- Security Onion displayed the error: “The management IP could not be determined.”  
- I was unable to access the web UI until the network settings were fixed.

🟢 Resolution:

- Reconfigured the VM network adapters before restarting the installation.  
- Ran the Security Onion installer again with the correct network configuration.  
- Verified that the management IP was detected correctly and the web UI became accessible.

**Lesson Learned:**  

This incident reinforced the importance of planning network configurations before installation. Changing IP settings mid-install can prevent the system from detecting key interfaces, causing errors and temporary access loss. In the future, I’ll make sure static IPs, gateways, and adapter setups are correct from the start to avoid troubleshooting delays and ensure smooth deployments.


## SO Management IP Detection Failure - Update

Date:
9/9/2025

🔴 Cause:

- I mistakenly used the same VirtualBox Host-Only IP for both the static IP and the gateway.

🟡 Impact:

- Security Onion displayed the error: “The management IP could not be determined.”  
- Setup could not proceed.  
- Continuous IP redirects occurred.  
- I attempted to change adapter attachment order.  
- I manually changed the Host-only IP from an APIPA address to a reachable IP.  
- Eventually, I removed the SO VM and repaired VirtualBox.exe.

🟢 Resolution:

- Created a unique IPv4 management IP separate from the gateway.  
- Verified that the VM and host could communicate and that NAT redirections worked correctly.

**Lesson Learned:**  

This was a huge learning opportunity. While reviewing installation logs and using `ip addr`, I realized both my `enp0s3` and `enp0s8` interfaces had the same IP, which I didn’t fully understand at first. I also misunderstood CIDR notation, thinking `/24` was a 4-octet address; I understand that it represents a 24-bit subnet mask. These mistakes caused confusion in network routing and setup failures.  

Going forward, I now clearly understand the difference between static IP, gateway, and subnet, and I’ll ensure no IP conflicts exist before installation. 


## Reflection and Next Steps
Date: 11/10/2025

Despite repeated attempts, I wasn’t able to get Security Onion’s GUI running in my lab. At first, I thought about removing this journal, but I realized that documenting the struggle is just as important as documenting the wins. Cybersecurity isn’t about flawless execution, it’s about persistence, troubleshooting, and learning from every misstep. This process gave me valuable insight into installation requirements, networking dependencies, and the challenges analysts face when building monitoring environments. Even though the outcome wasn’t what I hoped for, the lessons I captured here will guide me in future builds and strengthen my problem-solving approach.

Moving forward, I plan to explore other SOC platforms such as Wazuh, and Splunk, while continuing hands-on practice through TryHackMe and other Blue Team online resources. My focus remains clear: building the skills to investigate alerts, understand signals, and respond effectively to incidents. This journal represents more than a failed install, it’s proof of my resilience, documentation, and a commitment to growth. Success in cybersecurity isn’t a straight line; it’s a series of iterations, and each one brings me closer to mastery.