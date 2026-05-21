# Enterprise IT Support & Identity Management Sandbox
Active Directory Homelab, DNS, DHCP, GP, Etc
Active Directory Home Lab (VirtualBox)
# Active Directory Home Lab (VirtualBox)

---------------------------------------

Overview

In this project, I built a small corporate-style Active Directory environment using VirtualBox, Windows Server 2022, and Windows 10.
The goal of this lab was to practice core Windows Server administration and networking concepts commonly used in IT Support, Help Desk, and System Administration roles.

This lab includes:

•	- Active Directory Domain Services (AD DS)
•	- DNS
•	- DHCP
•	- NAT/Routing
•	- Domain-joined Windows client
•	- Bulk user creation with PowerShell
•	- Internal virtual networking
•	- Group policies


Lab Topology

<img width="1630" height="965" alt="lab" src="https://github.com/user-attachments/assets/ce9b0a6e-1933-4298-b815-00539c6382de" />


Technologies Used
•	- Oracle VirtualBox
•	- Windows Server 2022
•	- Windows 10 Pro
•	- Active Directory
•	- DHCP
•	- DNS
•	- PowerShell
•	- NAT / Routing and Remote Access


What I Configured

1. Instalation & download


I installed:

•	- Oracle VirtualBox
•	- VirtualBox Extension Pack

I downloaded:

•	- Windows Server 2022 ISO
•	- Windows 10 Pro ISO


2. Created the Domain Controller VM

I created a virtual machine named: winDC


<img width="1280" height="749" alt="vlcsnap-2026-05-12-22h29m07s126" src="https://github.com/user-attachments/assets/9d888dba-17c2-497a-b40a-44b765b92f86" />

Configuration:
•	- 4 GB RAM
•	- Multiple CPU cores
•	- 2 network adapters

Network adapters:
•	- NAT adapter for internet access
•	- Internal Network adapter for the private lab network

<img width="1271" height="742" alt="vlcsnap-2026-05-12-22h40m24s069" src="https://github.com/user-attachments/assets/4936672d-0288-4f9f-a794-dba913b4a7df" />

<img width="1270" height="736" alt="vlcsnap-2026-05-12-22h40m41s852" src="https://github.com/user-attachments/assets/3e8a4553-6a96-45c5-ad3a-9ef1ddc17f0a" />


3. Installed Windows Server 2022

<img width="1025" height="857" alt="vlcsnap-2026-05-12-22h45m17s479" src="https://github.com/user-attachments/assets/f6b777a3-f0c0-4c63-9a7d-d306948a61b7" />


I installed:

Windows Server 2022 Standard (Desktop Experience)

After installation:

•	- Set Administrator password

<img width="1026" height="857" alt="vlcsnap-2026-05-12-22h47m26s667" src="https://github.com/user-attachments/assets/4625859a-20b8-47b1-9040-a92c31c74f4c" />

•	- Installed VirtualBox Guest Additions
<img width="1026" height="853" alt="vlcsnap-2026-05-12-22h49m43s174" src="https://github.com/user-attachments/assets/912a6825-41c7-40e1-8ad5-6611d434d7b0" />
<img width="1011" height="853" alt="vlcsnap-2026-05-12-22h50m14s317" src="https://github.com/user-attachments/assets/49e09e68-c5a6-491a-8bb1-b77ccb5804e8" />

•	- Restarted the VM

<img width="1018" height="847" alt="vlcsnap-2026-05-12-22h50m41s797" src="https://github.com/user-attachments/assets/cd39af82-5820-4d90-a2d0-7ae50d03c2ba" />

4. Configured Networking

I renamed the network adapters for easier management:

<img width="1118" height="631" alt="vlcsnap-2026-05-12-23h15m15s527" src="https://github.com/user-attachments/assets/2108cbf0-f420-46cb-a30e-69d8ec4644fb" />

•	- INTERNET
•	- INTERNAL

I configured a static IP address on the internal adapter:

<img width="1162" height="952" alt="vlcsnap-2026-05-12-23h19m58s598" src="https://github.com/user-attachments/assets/e7784e63-155c-429a-969e-52c167e7b48f" />

IP Address: 172.16.0.1
Subnet Mask: 255.255.255.0
DNS Server: 127.0.0.1
I left the default gateway blank because the server itself would handle routing.

I Renamed the PC to DomainC

<img width="1239" height="947" alt="vlcsnap-2026-05-12-23h23m29s043" src="https://github.com/user-attachments/assets/d010c21b-cf7f-4bd6-8513-67ae107bbee0" />

5. Installed Active Directory Domain Services

Using Server Manager, I installed:
Active Directory Domain Services (AD DS)
<img width="2555" height="1346" alt="vlcsnap-2026-05-12-23h25m58s424" src="https://github.com/user-attachments/assets/202842e0-ae01-44ba-892a-89e5f31288de" />

I promoted the server to a Domain Controller and created a new forest:
mydomain.com
<img width="774" height="545" alt="vlcsnap-2026-05-12-23h27m43s430" src="https://github.com/user-attachments/assets/f1225022-d980-40e7-ae83-67b3d0d7a9a3" />

<img width="1193" height="806" alt="vlcsnap-2026-05-12-23h29m19s297" src="https://github.com/user-attachments/assets/6bff0a3f-ed54-43f2-9437-d6e62f424614" />

6. Created Administrative Accounts

I created:
•	- A dedicated Organizational Unit (OU)
<img width="2560" height="1389" alt="vlcsnap-2026-05-12-23h33m23s973" src="https://github.com/user-attachments/assets/6a96bac6-29d2-4d48-81a5-20d1839c6e0c" />

•	- A custom domain admin account
<img width="2560" height="1391" alt="vlcsnap-2026-05-12-23h34m27s526" src="https://github.com/user-attachments/assets/39ccc8a0-0881-4368-b193-fc6f9f524377" />

I added the account to:
Domain Admins
<img width="2560" height="1389" alt="vlcsnap-2026-05-12-23h35m56s889" src="https://github.com/user-attachments/assets/42d98956-7616-40dd-9ec2-5befbf110bf3" />

This allowed me to manage the domain using a separate admin account instead of the built-in Administrator account.
 <img width="2370" height="1363" alt="vlcsnap-2026-05-12-23h39m05s320" src="https://github.com/user-attachments/assets/e7cab7e8-1a36-4882-8d15-73560ac24c2a" />
 

7. Configured NAT and Routing

I installed:

Remote Access
<img width="1124" height="858" alt="vlcsnap-2026-05-12-23h41m33s964" src="https://github.com/user-attachments/assets/1074c126-6a2d-416d-8299-b1fd1b69c823" />
<img width="1063" height="828" alt="vlcsnap-2026-05-12-23h42m40s507" src="https://github.com/user-attachments/assets/3a140b86-3e11-49fa-9205-880bbb40b827" />
Then enabled:
•	- NAT
•	- Routing and Remote Access

<img width="1230" height="930" alt="vlcsnap-2026-05-12-23h45m02s742" src="https://github.com/user-attachments/assets/a545a55c-2352-47c6-af42-374428c03cf9" />

This allowed internal client machines to access the internet through the Domain Controller.


8. Configured DHCP
<img width="976" height="726" alt="vlcsnap-2026-05-12-23h47m15s765" src="https://github.com/user-attachments/assets/e9d2ffd8-596d-4962-bafa-436404da74dd" />

I installed the DHCP role and configured a scope:

172.16.0.100 - 172.16.0.200
<img width="1144" height="733" alt="vlcsnap-2026-05-12-23h49m15s245" src="https://github.com/user-attachments/assets/9b2fbebc-d9e4-4c34-ae58-1399e5e0c354" />

DHCP settings included:
•	- Default Gateway: 172.16.0.1
•	- DNS Server: 172.16.0.1
<img width="1071" height="771" alt="vlcsnap-2026-05-12-23h50m57s589" src="https://github.com/user-attachments/assets/4424923b-c127-411a-aa97-f4f8c2ea5835" />

This allowed client machines to automatically receive:
•	- IP addresses
•	- DNS settings
•	- Gateway information
<img width="1056" height="794" alt="vlcsnap-2026-05-12-23h52m42s528" src="https://github.com/user-attachments/assets/34af70de-e98a-4f28-b973-e6579e9aa31f" />


9. Bulk User Creation with PowerShell


[PowerShell Script](https://github.com/joshmadakor1/AD_PS)


I used a PowerShell script to automatically create over 1000 Active Directory users.

The script:

•	- Imported names from a text file

•	- Created usernames automatically

•	- Assigned passwords

•	- Added users into a dedicated OU

<img width="935" height="675" alt="vlcsnap-2026-05-13-00h01m27s331" src="https://github.com/user-attachments/assets/45ead618-f970-493f-992a-32ede1d2155f" />


Example username format:

ienache

This helped me practice:

•	- PowerShell scripting

•	- Active Directory automation

•	- Bulk user management





11. Created Windows 10 Client VM



I created a second VM named: client

Configuration:
•	- Windows 10 Pro

•	- Internal Network adapter only


The client automatically received:

•	- An IP address from DHCP

•	- DNS settings

•	- Internet connectivity through NAT


<img width="2512" height="1113" alt="vlcsnap-2026-05-13-00h10m19s329" src="https://github.com/user-attachments/assets/4789698a-30d5-4c47-a49d-208516daff0e" />


11. Joined the Client to the Domain

I renamed the client machine: CLIENT1

Then joined it to:
mydomain.com

<img width="1217" height="1135" alt="vlcsnap-2026-05-13-00h13m25s104" src="https://github.com/user-attachments/assets/d0feca32-aa15-4ddd-8461-dbd20c69d863" />


After restarting, I was able to log in using domain user accounts created earlier in Active Directory.

<img width="1208" height="1148" alt="vlcsnap-2026-05-13-00h14m51s668" src="https://github.com/user-attachments/assets/a5f7e4ac-3a98-4b1f-81e8-888dd6a5ecd8" />


12. Verification and Testing

I verified:

•	- DHCP leases

•	- DNS resolution

•	- Internet connectivity

•	- Domain authentication

•	- Domain-joined computer objects in Active Directory


---------------------------------------

Commands used:

ipconfig

ping google.com

ping mydomain.com

whoami


---------------------------------------


This project helped me practice and understand:

•	- Active Directory administration

•	- Windows Server installation and configuration

•	- DHCP configuration

•	- DNS configuration

•	- NAT and routing

•	- PowerShell scripting

•	- User and computer management

•	- Domain joining

•	- Virtual networking

•	- Troubleshooting Windows networking issues


---------------------------------------


Through this lab, I gained hands-on experience with how enterprise Windows environments function in real-world corporate networks.

I also learned:

•	- How centralized authentication works

•	- How domain users can log into multiple systems

•	- How DHCP and DNS interact in Active Directory environments

•	- How PowerShell can automate repetitive administrative tasks


---------------------------------------
Possible future additions:

•	- Group Policy Objects (GPOs)

•	- File shares and permissions

•	- WSUS

•	- VPN configuration

•	- SIEM integration

•	- Windows Server backups

•	- Additional client machines

•	- Security hardening



Stay tuned.

