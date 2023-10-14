<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
Virtualize AD Home Lab with Virtualbox. Create an OU and add 1,000 users to it with a PowerShell script. Implement RAS, NAT and DHCP on Domain Controller and join a client workstation to the domain on an internal network. <br />

<h2>Languages and Utilities Used</h2>
- <b>PowerShell</b> 

<h2>Environments Used </h2>
- <b>Windows 11</b> (22H2)

<h2>Diagram </h2>
<img src="https://i.imgur.com/4ETz4iH.png" height="60%" width="60%" />

<h2>Walk-through:</h2>
<p align="center">
 
 [Download VitualBox and Virtualbox Extension Pack](https://www.virtualbox.org/wiki/Downloads)<br />
 [Download Windows 11 ISO](https://www.microsoft.com/software-download/windows11)<br />
 [Download Windows Server 2022 Evaluation ISO](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022)<br />
 [Download PS script and text file with usernames](https://github.com/jwczerwinski/AD_PS-master/raw/main/AD_PS-master.zip)

<br />
<br />
Start Virtualbox and create VM for Domain Controller: <br/>
<img src="https://i.imgur.com/Kiz6sxF.png" height="60%" width="60%" />
<img src="https://i.imgur.com/8uGA2qf.png" height="60%" width="60%" />
<img src="https://i.imgur.com/c9lkfQ1.png" height="60%" width="60%" />
<br />
<br />
In Domain Controller settings create second NIC for internal network:  <br/>
<img src="https://i.imgur.com/8ZqrXO9.png" height="60%" width="60%" />
<br />
<br />
Start Domain Controller and select bootable Windows Server ISO:  <br/>
<img src="https://i.imgur.com/NQKBYBe.png" height="60%" width="60%" />
<br />
<br />
During installation select Windows Server 2022 Standard (Desktop Experience):  <br/>
<img src="https://i.imgur.com/11AWveb.png" height="60%" width="60%" />
<br />
<br />
Install VirtualBox Windows Guest Additions then restart VM:  <br/>
<img src="https://i.imgur.com/xs9O72B.png" height="60%" width="60%" />
<img src="https://i.imgur.com/enoirxx.png" height="60%" width="60%" />
<br />
<br />
Rename Server then restart VM:  <br/>
<img src="https://i.imgur.com/rPvMkbl.png" height="60%" width="60%" />
<br />
<br />
Change both NICs names. For internal NIC, assign private static IP address and DNS loopback address:  <br/>
<img src="https://i.imgur.com/nywytD6.png" height="60%" width="60%" />
<img src="https://i.imgur.com/EPzwRov.png" height="60%" width="60%" />
<br />
<br />
Add roles and features > install "Active Directory Domain Services":  <br/>
<img src="https://i.imgur.com/KOdPcd3.png" height="60%" width="60%" />
<br />
<br />
Post-deployment Configuration > Promote this server to a domain controller. Add a new forest. Assign root domain name. Install and restart VM:  <br/>
<img src="https://i.imgur.com/j7unu2L.png" height="60%" width="60%" />
<img src="https://i.imgur.com/UxFtv0S.png" height="60%" width="60%" />
<br />
<br />
Create OU for admin. Create admin user in OU. Add admin user to Domain Admins group:  <br/>
<img src="https://i.imgur.com/nQqweTs.png" height="60%" width="60%" />
<br />
<br />
Sign into Server with new admin user:  <br/>
<img src="https://i.imgur.com/RKBUPC2.png" height="60%" width="60%" />
<br />
<br />
Add roles and features > install "Remote Access" and "Routing" (RAS, Remote Access Service) and NAT for internet NIC:  <br/>
<img src="https://i.imgur.com/qbEDCH3.png" height="60%" width="60%" />
<img src="https://i.imgur.com/xJlpZmm.png" height="60%" width="60%" />
<img src="https://i.imgur.com/fMR4CR2.png" height="60%" width="60%" />
<img src="https://i.imgur.com/kCyXyaP.png" height="60%" width="60%" />
<img src="https://i.imgur.com/6oVTgos.png" height="60%" width="60%" />
<img src="https://i.imgur.com/lFdGzVT.png" height="60%" width="60%" />
<br />
<br />
Add roles and features > install DHCP server:  <br/>
<img src="https://i.imgur.com/akONNN4.png" height="60%" width="60%" />
<br />
<br />
Tools dropdown menu > Setup DHCP server, IP address for router, IP address range, lease duration and router:  <br/>
<img src="https://i.imgur.com/D8awRyV.png" height="60%" width="60%" />
<img src="https://i.imgur.com/EA6NLMh.png" height="60%" width="60%" />
<img src="https://i.imgur.com/qcb4ou5.png" height="60%" width="60%" />
<img src="https://i.imgur.com/sYVtdTo.png" height="60%" width="60%" />
<img src="https://i.imgur.com/DkZVm20.png" height="60%" width="60%" />
<img src="https://i.imgur.com/peiojf4.png" height="60%" width="60%" />
<img src="https://i.imgur.com/ZBDx9Ab.png" height="60%" width="60%" />
<br />
<br />
Configure local server > turn off "Internet Explorer Enhanced Security Configuration":  <br/>
<img src="https://i.imgur.com/AI3dFA5.png" height="60%" width="60%" />
<br />
<br />
Add admin first and last name to "names" text file (see previously downloaded "AD_PS-master.zip"):  <br/>
<img src="https://i.imgur.com/V4DilVP.png" height="60%" width="60%" />
<br />
<br />
Run 1_CREATE_USERS.ps1 in PS:  <br/>
<img src="https://i.imgur.com/uUNnHHL.png" height="60%" width="60%" />
<img src="https://i.imgur.com/aYFOJNk.png" height="60%" width="60%" />
<img src="https://i.imgur.com/aKbkMoT.png" height="60%" width="60%" />
<br />
<br />
Create new VM for client workstation and connect to Domain Controllers internal NIC:  <br/>
<img src="https://i.imgur.com/cbwM4gZ.png" height="60%" width="60%" />
<img src="https://i.imgur.com/KltAGDM.png" height="60%" width="60%" />
<br />
<br />
Start client VM, install bootable Windows 11 ISO then select Windows 11 Pro and Custom Install in setup sequence:  <br/>
<img src="https://i.imgur.com/EzWQpMr.png" height="60%" width="60%" />
<img src="https://i.imgur.com/pVz8qKJ.png" height="60%" width="60%" />
<img src="https://i.imgur.com/EMGZMaf.png" height="60%" width="60%" />
<br />
<br />
Run ipconfig to confirm correct setup of IP addressing. Default gateway for router, ping 8.8.8.8 for DNS:  <br/>
<img src="https://i.imgur.com/1XD0dOA.png" height="60%" width="60%" />
<br />
<br />
Rename PC and join domain. Restart client VM:  <br/>
<img src="https://i.imgur.com/5Atuv59.png" height="60%" width="60%" />
<img src="https://i.imgur.com/FsCIdja.png" height="60%" width="60%" />
<br />
<br />
Verify on Domain Controller that client workstation VM was added to ADDS OUs Computers:  <br/>
<img src="https://i.imgur.com/0tyAPha.png" height="60%" width="60%" />
<br />
<br />
Verify on client VM by signing into client workstation with any user from automated PS script:  <br/>
<img src="https://i.imgur.com/4DWYdAH.png" height="60%" width="60%" />
<img src="https://i.imgur.com/jI0g41y.png" height="60%" width="60%" />
<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
