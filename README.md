<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
Create AD Home Lab with Virtualbox, Windows 11 and PowerShell.<br />

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 

<h2>Environments Used </h2>

- <b>Windows 11</b> (22H2)

<h2>Walk-through:</h2>

<p align="left">
 
 [Download VitualBox and Virtualbox Extension Pack](https://www.virtualbox.org/wiki/Downloads)<br />
 [Download Windows 11 ISO](https://www.microsoft.com/software-download/windows11)<br />
 [Download Windows Server 2022 Evaluation ISO](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022)

<br />
<br />
Start Virtualbox and create VM for Domain Controller: <br/>
<img src="https://i.imgur.com/Kiz6sxF.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8uGA2qf.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/c9lkfQ1.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
In Domain Controller settings create second NIC for internal network:  <br/>
<img src="https://i.imgur.com/8ZqrXO9.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start Domain Controller and select bootable Windows Server ISO:  <br/>
<img src="https://i.imgur.com/NQKBYBe.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
During installation select Windows Server 2022 Standard (Desktop Experience):  <br/>
<img src="https://i.imgur.com/11AWveb.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install VirtualBox Windows Guest Additions then restart VM:  <br/>
<img src="https://i.imgur.com/OCNkuPR.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/9c6fM4L.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Rename Server then restart VM:  <br/>
<img src="https://i.imgur.com/LX0dh2v.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Change NICs names and assign static IP address to internal NIC:  <br/>
<img src="https://i.imgur.com/rVbyoag.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/xWtZo7Q.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add roles and features > install "Active Directory Domain Services":  <br/>
<img src="https://i.imgur.com/mQ3sL5r.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Post-deployment Configuration > Promote this server to a domain controller. Add a new forest. Assign root domain name. Install and restart VM:  <br/>
<img src="https://i.imgur.com/nOOypmQ.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/sjuLFRM.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create OU for admin. Create admin user in OU. Add admin user to Domain Admins group:  <br/>
<img src="https://i.imgur.com/FA8Uys8.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sign into Server with new admin user:  <br/>
<img src="https://i.imgur.com/rwq1GUK.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add roles and features > install "Remote Access" and "Routing" (RAS, Remote Access Service) and NAT for internet NIC:  <br/>
<img src="https://i.imgur.com/F2Ha8ZD.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/UzI9rIu.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CR7hUCp.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DKaHSBz.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NieQq9B.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/gasAqmR.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add roles and features > install DHCP server:  <br/>
<img src="https://i.imgur.com/6hiotDq.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Tools dropdown menu > Setup DHCP server, IP address for router, IP address range and lease duration:  <br/>
<img src="https://i.imgur.com/r9yiFXl.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ZVdhkvJ.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Wiu4cxr.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/fgzgpyt.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4oJiXfc.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/gfdH0cS.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure local server > turn off "Internet Explorer Enhanced Security Configuration":  <br/>
<img src="https://i.imgur.com/AI3dFA5.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />

 [Download PS script and text file with usernames](https://github.com/jwczerwinski/AD_PS-master/raw/main/AD_PS-master.zip)

<br />
<br />
Create new VM with Windows 11:  <br/>
<img src="https://i.imgur.com/AI3dFA5.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure user and add Domain Controller RAS tools:  <br/>
<img src="https://i.imgur.com/AI3dFA5.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
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
