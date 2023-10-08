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
During installation select Windows Server 2022 Standard Evaluation:  <br/>
<br />
<br />
Change server name:  <br/>
<br />
<br />
Change NICs names and assign static IP address to internal NIC:  <br/>
<br />
<br />
Add roles and features > Active Directory Domain Servives:  <br/>
<br />
<br />
Promote Server to domain controller:  <br/>
<br />
<br />
Add new forest:  <br/>
<br />
<br />
Remote connect to domain controller from Windows 11 admin account:  <br/>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
