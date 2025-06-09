![1035255](https://github.com/user-attachments/assets/7cdae74a-7836-4365-af4e-737124531edf)

# Creating Users with Powershell
We will make configuration that allow Non-Admin domain users to let them log in to Client-1 via Remote Desktop. We’ll be able to create a whole bunch of users through powershell.<br />


<h2>Video Demonstration</h2>

-  ### [Google Drive: Creating Users with Powershell](https://drive.google.com/file/d/1a_LmNa_fqYY_LYJ2vTWzqOesSx0y66_n/view?usp=drive_link)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Resources Group, Virtual Machines/Computer, Virtual Machines/Window Server, Virtual Network and Subnet)
- Remote Desktop
- Active Directory Users and Computers (ADUC)
- Powershell

<h2>Operating Systems Used </h2>

- Windows 10 (Pro, version 22H2 - x64 Gen2)
- Windows Server 2022 Datacenter: (Azure Edition - x64 Gen2)

<h2>Creating Users Steps</h2>

- Step 1: Setup Remote Desktop for non-administrative users on Client-1
- Step 2: Create a bunch of additional users
- Step 3: Attempt to log into client-1 with one of the users

<h2>Lifecycle Stages</h2>

Step 1: Setup Remote Desktop for non-administrative users on Client-1
<p>
<img src="https://i.imgur.com/215Zki1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To allow non-administrative users to log into Client-1, log in as mydomain.com\jane_admin. Right click Start menu, Open System, go to Remote Desktop under Related Settings, and click Select Users. Click Add, type: "domain users", check the name, and confirm. This grants remote desktop access to all domain users. While Group Policy is typically used for this at scale, this manual method is sufficient for testing.
</p>
<br />

Step 2: Create a bunch of additional users
<p>
<img src="https://i.imgur.com/tClU2Ws.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, on DC-1, open PowerShell ISE as an administrator. Create a new script file by clicking the white page icon in the top-left corner and save it as "create users".
</p>
<br />

<p>
<img src="https://i.imgur.com/EdPKBtl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Then, visit the following GitHub link and copy the script: (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) Paste the script into your PowerShell ISE window and run it. This script will generate and create thousands of user accounts in the _EMPLOYEES OU.
</p>
<br />


Step 3: Attempt to log into client-1 with one of the users
<p>
<img src="https://i.imgur.com/94brhsC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the script has finished running (which may take around 8 minutes), open ADUC and navigate to the _EMPLOYEES OU to verify that the accounts have been created. Select one of the new accounts and attempt to log into Client-1 using the credentials: Username: mydomain.com\accountname, Password: Password1. This confirms that the domain and user provisioning are functioning correctly.
</p>
<br />
