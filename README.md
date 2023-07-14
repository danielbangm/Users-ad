<p align="center">
<img src="https://rb.gy/hdy7u" />
</p>

<h1>Active Directory - Post-Installation and Configuration</h1>

In this tutorial I will use Active directory in Azure to create a bunch of users and attempt to log into <b>client-1</b> with one of the users.

<h2>Objectives</h2>

-  More Experience with Azure (I will Create the environment here)
-  Understanding of the Domain Controler and DNS
-  Gain a better understanding of all parts of Active Directory such <b>resetting passwords<b> and <b>setting up users<b>.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Virtual Machine(DC-1)
- Virtual Machine(client-1)
- Remote Desktop
- Active Directory and Domain Services

<h2>Operating Systems Used</h2>

-  Windows Server 2022
-  Windows 10 pro

<h2>List of Prerequisites</h2>

-  All you need for this lab is to follow the <a href="https://github.com/danielbangm/configure-ad">first part </a>

<h2>Installation steps</h2>

-  Step 1: Create and Admin and Normal User Account in AD

I log into DC-1 with my username <b>daniel.com\labuser</b> because is now a Domain Controller and I go to Server Manager -> Active Directory Users and Computers. I Create 2 OU(Organizational Unit) called <b>_EMPLOYEES</b> and <b>_ADMINS</b>. Then I create a new employee named "Jane Doe" with the username "jane_admin" and add this username in the "Domain Admins" Security Group
![image](https://github.com/danielbangm/Users-ad/assets/22795502/6d9afafc-3fcd-4332-bf1c-0049b21961a0)

Now I log out/close the Remote Desktop Connection to DC-1and log back in as <b>daniel.com\jane_admin</b>. The user jane_admin will be my admin account from now

-  Step 2: Join Client-1 to the Domain (daniel.com)

I go to www.portal.azure.com and make sure I change Client-1's DNS settings to the DC-1's Private IP addressv(10.0.0.4). To do this just go to Client-1 -> Networking. Then change it. After Changing the DNS IP address I make sure I restart the Virtual Machine in Azure in order to flush the DNS cache.
![image](https://github.com/danielbangm/Users-ad/assets/22795502/23d2273e-d133-4345-bc7f-aa125cdb8fb6)

I use Remote Desktop Connection to connect to Client-1 and right click on Windows then System -> Rename this PC (advanced) -> Change -> daniel.com  It forces me to restart the computer.
![image](https://github.com/danielbangm/Users-ad/assets/22795502/8b940682-ba5c-4242-8130-04167ed0d093)
![image](https://github.com/danielbangm/Users-ad/assets/22795502/e59aabbe-ee73-47e7-a242-54ab07b31109)

I login to the Domain Controller via Remote Desktop to verify client-1 shows up in Active Directory Users and Computers inside the Computer container on the root of the domain.
![image](https://github.com/danielbangm/Users-ad/assets/22795502/d5d92da7-5b1f-4221-9457-98f2831ae3e1)

-  Step 3: Setup Remote Desktop for non-administrative Users on Client-1

I use Remote Desktop Connection to connect to Client-1 and right click on Windows then System -> Remote Desktop -> Allow Users to Remote Connect to this PC (advanced). Then I add "Domain Users". 
![image](https://github.com/danielbangm/Users-ad/assets/22795502/65e2d8c6-ffe2-4cca-893b-631ecdf56e97)

After this, I am now able to log into Client-1 as a normal, non-administrative user.

-  Step 4: Create a bunch of additional

I log into DC-1 as jane_admin, open the Powershell_ise as an administrator. 



