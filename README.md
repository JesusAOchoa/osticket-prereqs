<p align="center">
<img src="https://i.imgur.com/ZOUm27S.png" alt="osTicket logo"/>
</p>

<h1>osTicket -  Prerequisites and Installation</h1>
osTicket is a widely-used open-source support system that offers a seamless integration of inquiries generated through email, phone, and web-based forms into a user-friendly multi-user web interface. It provides a centralized platform to manage, organize, and archive all support requests and responses, allowing you to deliver high-quality service to your customers. This tutorial will guide you through the process of installing osTicket, including the prerequisites and necessary steps for setup..<br />

<h2>Technologies and Environments Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>
Good day and welcome to the first part of the tutorial!

Let's dive right in by creating a resource group and virtual machine (VM) in the Microsoft Azure portal. This way, we can protect our physical machine and ensure a smooth process. We'll connect to the VM using Remote Desktop Protocol (RDP) for the next steps in our tutorial.

<img src="https://i.imgur.com/quWtguU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, all you need to do is connect to our freshly created VM using RDP and the VM's public IPv4 address. Just a quick note: if you're using a Mac, make sure to download Microsoft RDP in order to establish a remote connection to the VM.
 
<img src="https://i.imgur.com/jcHgeUc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

Great!  Now that you are in your VM you will have to enable **IIS (Internet Information Services)**. To do so, 1-Access the Control Panel > 2-Program > 3-On the upper left hand side select **"Turn Windows features On or Off"**> 4- Enable the **IIS** (Internet Information Services) > 5-Expand the World Wide Web Services > 6-Expand Application Development features > 7-Check the **CGI box and click OK to install**.


<img src="https://i.imgur.com/WTZReTK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, install web platform installer
</p>
<br />
<p>
<img src="https://i.imgur.com/nBYUaCi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
From the installation files, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

<p>
<img src="https://i.imgur.com/NHm3jYC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
From the installation files, install the Rewrite Module (rewrite_amd64_en-US.msi)

<p>
<img src="https://i.imgur.com/ONqi3c8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p></p>
<br />
Create the directory C:\PHP

From the installation files, unzip PHP 7.3.8(phph-7.3.8-nts-Win32-VC15-x86.zip) into the C:/PHP directory you created.

<p>
<img src="https://i.imgur.com/q5e5xS1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
From the installation files install VC_redist.x86.exe.

<p>
<img src="https://i.imgur.com/0HP8dI0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
From installation files install MySQL 5.5.62 (mysql-5.5.62-win32.msi)

Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1

<p>
<img src="https://i.imgur.com/dphcuFU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

<p>
<img src="https://i.imgur.com/J7DbWem.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
 Open IIS as an Admin, register PHP, then restart the server

<p>
<img src="https://i.imgur.com/fNTPqs0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<p>
<img src="https://i.imgur.com/GyjOR7a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />
Install osTicket v1.15.8

Go back into IIS manager and enable some extensions. To do this you have to go to Sites->Default->osTicket Then double click on PHP manager. Click on **Disable or enable an extension** Enable  "phph_imap" - "php_intl.dll"  &  "php_opcache.dll" then refresh the osTicket webserver and obsereve the changes.

<p>
<img src="https://i.imgur.com/4My1W0a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />


Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php Assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all
<p>
<img src="https://i.imgur.com/K8rJfTj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />


Once you've made the necessary changes to the ost-config.php file, click on the "Continue" button. You should be greeted with the following screen:

<p>
<img src="https://i.imgur.com/ezp9fFm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>Once the above information is filled in click save changes at the bottom of the screen
<br />
After saving you should see this screen. Click continue at the bottom of the screen

<p>
<img src="https://i.imgur.com/SafFTug.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

Great job! You have successfully completed the installation of osTicket. Congratulations!
<p>
<img src="https://i.imgur.com/8QmIKZo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

To begin, install HeidiSQL using the installation files. After the installation is complete, open HeidiSQL. Within HeidiSQL, create a new session with the credentials "root" for the username and "Password1" for the password. Connect to the session and proceed to create a database named "osTicket"(AND MAKE SURE IT SAIS OSTICKET).

<img src="https://i.imgur.com/qcY4V4w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

LETS GO! You have now installed osTicket

Thanks for reading!
For the the next tutorial go [here](https://github.com/JesusAOchoa/post-install-config)
