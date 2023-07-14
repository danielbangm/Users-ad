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

First I am going to www.portal.azure.com and set Client-1's DNS settings to DC-1's Private IP address
