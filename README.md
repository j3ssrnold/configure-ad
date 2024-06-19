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

Step 1: To get started with an on-premises Active Directory within Azure Virtual Machines (VM), go to the [Azure Portal](https://portal.azure.com). You will begin by creating the Domain Controller VM.

-  In the VM Tab --> Click Create Machine --> Enter Resource Group Name as **AD-Lab** --> Name the VM as **DC-1** --> Select **Windows Server 2022 Datacenter**.     

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
>If the Network does not match, you may have attemped to create your Windows VM too soon after Domain Controller deployment. Go back to VM screen and give Azure a few more moments. After this, you should try to create your Windows VM again. Your Networks should match.

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

Step 4: Connect to Client-1 VM

-  Head back to VM page --> Select Client-1--> Remote Desktop Connection - Connect --> Select Yes on validation certificate. 

<p>
<img src="https://i.imgur.com/8Gf0O4e.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/QyJr0QQ.png" title="source: imgur.com" /></a>
</p>

-  Login pop-up window --> More Users --> Use Different Account --> Enter Username/Password you used when creating VM --> Click OK

<p>
<img src="https://i.imgur.com/PDpaLCd.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/ZaGSR8w.png" title="source: imgur.com" /></a>
</p>
<br />

Step 5: Ensure Connectivity Between Client-1 and Domain Controller.

- Go down to Search bar and type in **cmd**. Open Command Prompt. Perpetual ping DC-1s private IP address ***10.0.0.4***.

<p>
<img src="https://i.imgur.com/bNDCVit.png" title="source: imgur.com" /></a>
</p>

>[!Note]
>You should get a return of **Request Timed Out**; which means you are not yet connected to the Domain Controller.

-  Login to your DC-1 VM using Remote Desktop Connection --> Enter the username/password you selected during creation --> Select OK.
  
<p>
<img src="https://i.imgur.com/4GNhdqP.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/ZaGSR8w.png" title="source: imgur.com" /></a>
</p>

-  Your DC-1 home screen display should look like this:

<p>
<img src="https://i.imgur.com/kpvu0ox.png" title="source: imgur.com" /></a>  
</p>

-  In the search bar type in ***wf.msc*** to bring up your Windows Firewall --> Select Inbound Rules.

<p>
<img src="https://i.imgur.com/2XOFJ3V.png" title="source: imgur.com" /></a>
</p>

-  Select Protocol to organize --> Choose Both Core Networking Diagnostic options --> Enable Rule 

<p>
<img src="https://i.imgur.com/2WR5weG.png" title="source: imgur.com" /></a>
</p>

- Go back to Client-1 command prompt to check connectivity. You can see a return on the ping so your connection is successful. You can always CTRL+C to stop the ping.

<p>
<img src="https://i.imgur.com/ypddqUD.png" title="source: imgur.com" /></a>
</p>
<br />

Step 6: Next you will want to install Active Directory on your Domain Controller.

-  Head back to DC-1. Select Add New Roles and Features --> Next to begin proceeding through install screens.

<p>
<img src="https://i.imgur.com/M7FSrkl.png" title="source: imgur.com" /></a>
</p>

-  Server Roles Window --> Active Directory Domain Services --> Add Features.

<p>
<img src="https://i.imgur.com/DZC1S4f.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/C47czEP.png" title="source: imgur.com" /></a>
</p>

- In the Confirmation Window --> Install. Allow the Wizard to complete installation --> Close

<p>
<img src="https://i.imgur.com/C0Pzgq2.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/w5qmmT8.png" title="source: imgur.com" /></a>
</p>
<br />

Step 7: Promoting the Server to a Domain Controller.

-  In the top right of the window you should see a flag with a yellow exclamaition point. Click that flag --> Promote.

<p>
<img src="https://i.imgur.com/3Hbyo2u.png" title="source: imgur.com" /></a>
</p>

-  A configuration wizard pops up. You will need to add a new forest as **mydomain.com**. (You can name it whatever you wish).

<p>
<img src="https://i.imgur.com/ZKWzHzc.png" title="source: imgur.com" /></a>
</p>

- In the Domain options window, enter in your password for the Domain Controller.

<p>
<img src="https://i.imgur.com/74M6vcj.png" title="source: imgur.com" /></a>
</p>

-  Hit next until you get to the Additional options window. Allow the wizard to autopopulate the NetBIOS domain name. Click Next.

<p>
<img src="https://i.imgur.com/kofdL1d.png" title="source: imgur.com" /></a>
</p>

-  Allow the wizard to do the prerequisite check, then install. The computer will restart once complete, which means for your VM will log you off.

<p>
<img src="https://i.imgur.com/3qF7quK.png" title="source: imgur.com" /></a>
</p>

-  Log back in to DC-1 as mydomain.com/labuser.

<p>
<img src="https://i.imgur.com/ZaGSR8w.png" title="source: imgur.com" /></a>
</p>

>[!TIP]
>Be sure to use the same password that you used when creating the DC-1 VM.
<br />

Step 8: Add an Admin and Normal Users in Active Directory

-  Once Back at the Server home screen, in the top right corner click tools --> Active Directory Users and Computers.
  -  Click mydomain.com --> right click new --> Organizational Unit (OU) --> then enter _EMPLOYEES for your new folder.

<p>
<img src="https://i.imgur.com/UIZLvrN.png" title="source: imgur.com" /></a>
</p>

-  Add another OU --> Name it _ADMINS.

<p>
<img src="https://i.imgur.com/mY5fNgR.png" title="source: imgur.com" /></a>
</p>

-  Create an Admin. _ADMINS folder --> right click New --> Add User --> Enter in the information for (Jane Doe), your Admin. Click Next.

<p>
<img src="https://i.imgur.com/4qocEdj.png" title="source: imgur.com" /></a>
</p>

-  Be sure to uncheck user must change password at next logon --> Click Next. 

<p>
<img src="https://i.imgur.com/CEusfvw.png" title="source: imgur.com" /></a>
</p>

-  Click Finish to Create your new Admin.

<p>
<img src="https://i.imgur.com/X26JXoo.png" title="source: imgur.com" /></a>
</p>

-  Don't Forget to Add Jane to Domain Admins. Right Click Jane Doe --> Properties --> Member of --> Add

<p>
<img src="https://i.imgur.com/8dAkPBT.png" title="source: imgur.com" /></a>
</p>

-  Enter domain admins --> Check Names --> Click OK.

<p>
<img src="https://i.imgur.com/XOiizHj.png" title="source: imgur.com" /></a>
</p>

-  CLick apply --> OK.

<p>
<img src="https://i.imgur.com/8dAkPBT.png" title="source: imgur.com" /></a>
</p>

>[!IMPORTANT]
>Use jane_admin as your admin account for the rest of the tutorial.
<br />

Step 9: Join Client-1 to your domain (mydomain.com).

-  Click on Client-1 in the VM tab --> Network Settings --> Network Interface --> DNS Servers --> Custom Server --> DC-1's Private IP address --> Save.

<p>
<img src="https://i.imgur.com/Sl1BsVt.png" title="source: imgur.com" /></a>
</p>

-  Click Restart --> Yes to restart machine.

<p>
<img src="https://i.imgur.com/FKMv8Cf.png" title="source: imgur.com" /></a>
</p>

-  Login to Client-1 as labuser (original local admin) --> Settings --> Rename this pc (advanced).

<p>
<img src="https://i.imgur.com/zaejwAK.png" title="source: imgur.com" /></a>
</p>

-  In the System Properties window select Change.
  -  In Command Prompt (CMD) --> ipcongfig /all to find the DNS Server IP address.

<p>
<img src="https://i.imgur.com/RktHduF.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/Brc9Lse.png" title="source: imgur.com" /></a>
</p>

-  In the pop-up enter in the DNS Server address **10.0.0.4**. Click OK.

<p>
<img src="https://i.imgur.com/xbMrKjS.png" title="source: imgur.com" /></a>
</p>

-  Allow Jane access to the domain. Enter in her credentials and click ok. Your computer (VM) will restart.

<p>
<img src="https://i.imgur.com/s7cZNbH.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/IOG3602.png" title="source: imgur.com" /></a>
</p>

- Login to DC-1 as with Jane using mydomain.com\jane_admin. Verify that Client-1 shows up in Active Directory Users and Computers (ADUC).
  -  Tools --> ADUC --> mydomain.com --> Computers.
    -  mydomain.com --> New OU --> _CLIENTS --> Select Client-1 in ***Computers*** --> Move to _CLIENTS for organization.

<p>
<img src="https://i.imgur.com/S4gtvgv.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/tLpZXV5.png" title="source: imgur.com" /></a>
</p>
<br />

Step 10: Setup Remote Desktop for Normal Users on Client-1

-  Login to Client-1 using the admin account: mydomain.com\jane_admin. Open System Properties.

<p>
<img src="https://i.imgur.com/UvwP4yt.png" title="source: imgur.com" /></a>
</p>

-  Remote Desktop --> User Accounts --> Add --> Enter Domain Users --> Check Names --> OK --> OK again.

<p>
<img src="https://i.imgur.com/xZKgQXE.png" title="source: imgur.com" /></a>
</p>

-  Enter Domain Users --> Check Names --> OK --> OK again. You can now log-in to Client-1 as a normal user now.

<p>
<img src="https://i.imgur.com/OgQ0dJO.png" title="source: imgur.com" /></a>
<img src="https://i.imgur.com/6i4Bz1Z.png" title="source: imgur.com" /></a>
</p>
<br />

Step 11:  Finally, use Poweshell to facilitate Mass Account Creation and log-in as a random user.

-  Login to DC-1 as jane_admin. Open Powershell_ISE as administrator.

<p>
<img src="https://i.imgur.com/IQafNoF.png" title="source: imgur.com" /></a>
</p>

-  Head to [this script file](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1). Copy the raw data file.

<p>
<img src="https://i.imgur.com/TQWStxy.png" title="source: imgur.com" /></a>
</p>

>[!IMPORTANT]
>Be sure to note the passoword at the beginning of the script.

-  Insert the raw data into Powershell --> Run --> Watch as Powershell generates accounts.

<p>
<img src="https://i.imgur.com/w0585Eh.png" title="source: imgur.com" /></a>
</p>

-  Go back to ADUC --> _EMPLOYEES --> select a random user to log into Client-1 with.

<p>
<img src="https://i.imgur.com/eNdIYpG.png" title="source: imgur.com" /></a>
</p>

- Login to Client-1 as the user you selected --> mydomain.com\bal.dudi. Enter the Password at the beginning of the script file.

<p>
<img src="https://i.imgur.com/JmhzsKP.png" title="source: imgur.com" /></a>
</p>
<br />

Congratulations! You have now completed the Active Directory Implementation Tutorial!
