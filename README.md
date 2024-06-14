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
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Resource/Connectivity Setup
- Active Directory Installation
- Administrator/User Configuration
- Powershell And Mass Account Creation

<h2>Deployment and Configuration Steps</h2>

Step 1: To get started with an on-premises Active Directory within Azure Virtual Machines (VM), go to [portal.azure.com](https://portal.azure.com). First you need to create the VM Domain Controller.

-  In the Virtual Machines Tab, Click Create Machine --> Enter Resource Group Name as **AD-Lab** --> Name the VM as **DC-1** --> Select **Windows Server 2022 Datacenter**.     

<p>
<img src="https://i.imgur.com/WJW9V4h.png" title="source: imgur.com" /></a>
</p>

-  Create a Username and Password.

<p>
<img src="https://i.imgur.com/MTtx8Pp.png" title="source: imgur.com" /></a>
</p> 

-  Click next ***twice*** to get to the Networking Tab. Click Review and Create.

<p>
<img src="https://i.imgur.com/IWsnGzN.png" title="source: imgur.com" /></a>
</p>

>[!IMPORTANT]
>***Take note of both the Resource Group and Network that the Controller is assigned to in the images above. You will need these later to create your Windows 10 VM***

-  Now that your Domain Controller has been validated - Create your Machine.

<p>
<img src="https://i.imgur.com/VR8LUAp.png" title="source: imgur.com" /></a>
</p>
<br />

Step 2: Create the Client VM. Go back to the Virtual Machines Tab and click Create Azure Machine. 

-  Be sure that the Resource Group is **AD-Lab** --> Name the VM as **Client-1** --> Select **Windows 10 Pro (22H2)**.

<p>
<img src="https://i.imgur.com/H92tFrk.png" title="source: imgur.com" /></a>
</p>

-  Create username and password (you may keep the same for simplicity) --> Click next ***twice*** to navigate to the networking tab.

<p>
<img src="https://i.imgur.com/CFnd8LH.png" title="source: imgur.com" /></a>
</p>

-  Make sure the Network is the same as was created in DC-1 **(DC-1-vnet)**. Click Review + Create.

<p>
<img src="https://i.imgur.com/71tdtDC.png" title="source: imgur.com" /></a>
</p>

>[!TIP]
>If the Network does not match, you may have attemped to create your Windows VM too soon after Domain Controller Deployment. Go back to VM screen and give Azure a few more moments. After you should try to creat your Windows VM again. Networks should match now.

-  Now that your Windows VM has been validated - Create your machine.

<p>
<img src="https://i.imgur.com/Nq9Igq6.png" title="source: imgur.com" /></a>
</p>
<br />

Step 3: Set the Domain Controller's IP address to **static** to ensure that other devices can find this easily. This makes sure the process runs smoothly.

-  Go to the VM tab --> DC-1 --> Network Settings --> Network Interface
<p>
<img src="https://i.imgur.com/srrMp1p.png" title="source: imgur.com" /></a>
</p>

-  Click on ipconfig --> In the Edit pop-up under Allocation, Select static --> Enter private IP: 10.0.0.4 --> Save

<p>
<img src="https://i.imgur.com/RT0LUFU.png" title="source: imgur.com" /></a>
</p>
<br />

Step 4: Ensure connectivity between the Client and Domain Controller.

-  Go back to VM page --> 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
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
