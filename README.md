<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<!--<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute]/ !-->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Resource/Connectivity Setup
- Active Directory Installation
- Administrator/User Configuration
- Powershell And Mass Account Creation

<h2>Deployment and Configuration Steps</h2>

Step 1: To get started with an on-premises Active Directory within Azure Virtual Machines, go to [portal.azure.com](https://portal.azure.com). First you need to create the VM Domain Controller.

-  In the Virtual Machines Tab, Click Create Machine --> Enter Resource Group Name as <b>AD-Lab</b> --> Name the VM as DC-1 --> Select <b>Windows Server 2022 Datacenter</b>.     

<p>
<img src="https://i.imgur.com/WJW9V4h.png" title="source: imgur.com" /></a>
</p>

-  Create a username and password

<p>
<img src="https://i.imgur.com/MTtx8Pp.png" title="source: imgur.com" /></a>
</p> 

-  Click next **twice** to get to the Networking Tab. Click Review and Create.

<p>
<img src="https://i.imgur.com/IWsnGzN.png" title="source: imgur.com" /></a>
</p>

>[!IMPORTANT]
>***Take note of both the resource group and network that the Controller is assigned to in the images above. You will need these later to create your Windows 10 VM***

-  Now that your Domain Controller has been validated; Create your Machine.

<p>
<img src="https://i.imgur.com/VR8LUAp.png" title="source: imgur.com" /></a>
</p>
<br />

Step 2: 

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
