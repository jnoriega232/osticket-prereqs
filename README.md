<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system, osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Internet Information Services (IIS) with CGI in Windows
- PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Rewrite Module (rewrite_amd64_en-US.msi)
- PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
- VC_redist.x86.exe
- MySQL 5.5.62 (mysql-5.5.62-win32.msi)
- osTicket v1.15.8
- HeidiSQL
- Link to installation files: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

**Follow the steps in the order listed as almost any error will lead to having to start over from scratch in a new virtual machine!**

**Step 1:** Create a Windows 10</b> (21H2) virtual machine with 4vCPUs in your Microsoft Azure portal and connect via Remote Desktop. Do this by copy and pasting the public IP address in Remote Desktop Connection.
<p>
<img src="https://i.imgur.com/Nq0PrfI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Tb97pur.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

**Step 2:** Once up and running, install/enable "Internet Information Services" (IIS) in Windows with CGI: Control panel --> Programs --> Turn Windows features on or off --> check box titled "Internet Information Services" and expand --> expand "World Wide Web Services" --> expand "Application Development Features" --> check box titled "CGI".  IIS is a web server that allows your computer to serve up websites and because OsTicket runs out of a website, we need to setup and configure IIS.

<p align="center">
<img src="https://imgur.com/Pp3YiGv.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
<img src="https://i.imgur.com/dCCltnf.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
**Step 3:** Within your virtual machine using the installation files link, download and install:
- PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Rewrite Module (rewrite_amd64_en-US.msi)

  
**Step 4:** Create the directory C:\PHP.
<p align="center">
<img src="https://i.imgur.com/wQREDcc.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p align="center">

**Step 5:** From the installation files, download and install PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP. To do so, find php-7.3.8-nts-Win32-VC15-x86.zip in the Downloads folder, right-click and say extract all. You will browse to make the destination your C:\PHP folder.

<p>
<img src="https://i.imgur.com/h6Y5org.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

**Step 6:** From the installation files, download and install VC_redist.x86.exe.

**Step 7:** From the installation files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Choose Setup Type: Typical. Make sure to check the box "launch the MySQL Instance Configuration Wizard" after install. Continue setting up --> Next --> Standard Configuration --> check "Install As Windows Service" and leave Service Name MySQL --> You will then need to make some credentials. For the sake of this lab, we will use the username: root and the password: Password1. Lastly, Execute.

  
**Step 8:** Open Internet Information Services (IIS) as an Admin --> double-click PHP Manager --> register PHP from within IIS by selecting "Register new PHP version" --> browse C drive --> PHP --> select "php-cgi".

<p align="center">
<img src="https://i.imgur.com/Nf7FMrv.png" height="40%" width="40%" alt="osTicket Prereqs and Installation"/>
<img src="https://i.imgur.com/gm3nxWB.png" height="40%" width="40%" alt="osTicket Prereqs and Installation"/>
<img src="https://i.imgur.com/Ez5f7v4.png" height="40%" width="40%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

Follow up with reloading IIS: Click on the server "vm-osticket (vm-osticket\labuser)" --> click Restart

<p align="center">
<img src="https://i.imgur.com/vmupWzR.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

**Step 9:** Download osTicket v1.15.8 from the installation files and we need to extract and copy the "upload" folder to C:\inetpub\wwwroot. To do so open two separate File Explorer windows. On one go to C drive --> inetpub --> wwwroot. On the other File Explorer window go to Downloads --> double-click "osTicket-v1.15.8" --> click and drag the folder "upload" into the "wwwroot" folder on the other File Explorer window we opened. Now rename the folder "upload" to "osTicket".
  
<p align="center">
<img src="https://i.imgur.com/f4cXkg7.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
<img src="https://i.imgur.com/E12aErK.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

Follow up with reloading IIS: Click on the server "vm-osticket (vm-osticket\labuser)" --> click Restart.

**Step 10:** Go to Sites --> Default Web Site --> osTicket and click "Browse *:80" on the right hand side.

<p align="center">
<img src="https://i.imgur.com/iqCf28W.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>

A window should open in your browser appearing as below.

<p align="center">
<img src="https://i.imgur.com/3Iuh10I.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>


**Step 11:** Go back to Internet Information Services. Go to Sites --> Default --> osTicket and double-click the PHP Manager icon.

<p align="center">
<img src="https://i.imgur.com/mMpZQFr.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
Then, click "Enable or disable an extension" and enable the three extensions one at a time: *php_imap.dll*, *php_intl.dll*, and *php_opcache.dll* if they are not already so.
  
<p align="center">
<img src="https://i.imgur.com/UiRVoRw.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>
  
  
**Step 12:** Refresh the osTicket webpage. It should look something like this:
  
<p align="center">
<img src="https://i.imgur.com/lXPDFkX.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>
  
  
**Step 13:** Rename "C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php" to "C:\inetpub\wwwroot\osTicket\include\ost-config.php".
  
<p align="center">
<img src="https://i.imgur.com/Yb5ct3K.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>
  
  
Right-click ost-config.php, open Properties --> Security --> Advanced --> Permissions and click "Disable Inheritance" --> "Remove all inherited permissions from this object".
  
<p align="center">
<img src="https://i.imgur.com/yrLMEHU.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>
  
  
Then add new permissions for *everyone* and give *Full Control*. Under Permissions click Add --> Select a principal --> Enter the object name to select: type everyone and click Check Names --> OK --> check box for "Full Control" --> OK --> Apply --> OK --> OK.
  
<p align="center">
<img src="https://i.imgur.com/HE1qbyo.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
**Step 14:** Continue setting up osTicket in the browser. Go back to your browser and click "Continue". You should land at the page below. Fill out the first two sections: "System Settings" and "Admin User".
  
<p align="center">
<img src="https://i.imgur.com/yiCMjxE.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
**Step 15:** Download and install HeidiSQL from the installation files.

<p align="center">
<img src="https://i.imgur.com/9Vl5SUB.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
Then launch HeidiSQL --> click "New" in bottom left corner --> enter user and password: *root* and *Password1* --> click "Open".
  
<p align="center">
<img src="https://i.imgur.com/qiENBYr.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
Create a "New Database".
  
<p align="center">
<img src="https://i.imgur.com/UjyZNno.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
Name it "osTicket".
  
<p align="center">
<img src="https://i.imgur.com/kPHBdWx.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
**Step 16:** Go back to the browser and continue setting up osTicket by filling out the fields.
  
- Help Desk Name: *Name*'s Help Desk
- Default Email: Any email you want (nothing will be sent to it, just for practice)

- First Name: your first name
- Last Name: your last name
- Email Address: Any email you want (should be different from the Default Email)
- Username: I chose my name 
- Password: Password1
  
- MySQL Database: osTicket (the one you just created in HeidiSQL)
- MySQL Username: root
- MySQL Password: Password1
  
<p align="center">
<img src="https://i.imgur.com/MDf4OHc.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

  
Click "Install Now" and you should land at this page.
  
<p align="center">
<img src="https://i.imgur.com/o1ov4AR.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

Congratulations! You've successfully installed your own Help Desk Ticketing System!


Take note of these two links:
  
<p align="center">
<img src="https://i.imgur.com/xqOBpZL.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

"Your osTicket URL" takes you to the End User Portal where Users can create and submit tickets for assistance.

<p align="center">
<img src="https://i.imgur.com/ASpHU9g.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>
  
"Your Staff Control Panel" takes you to the Admin / Staff Portal where you can login and start working through tickets.

<p align="center">
<img src="https://i.imgur.com/LvqGC21.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>


**Now it's time to cleanup in preparation for Post-Installation Setup.** 

**Step 17:** Go to C:\inetpub\wwwroot\osTicket\setup folder. Delete only the "setup" folder itself.
  
<p align="center">
<img src="https://i.imgur.com/jMpbOyO.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>

**Finally:** Reset permissions for *Everyone* back to "read" and "read & execute" in C:\inetpub\wwwroot\osTicket\include\ost-config.php --> right-click "ost-config.php" --> properties --> Security --> Advanced --> select Everyone --> Edit --> check "read" and "read & execute" only --> OK --> Apply --> OK --> OK.

<p align="center">
<img src="https://i.imgur.com/9aYDI8d.png" height="50%" width="50%" alt="osTicket Prereqs and Installation"/>
</p>
<p>


🎉 **Congratulations on completing your osTicket Help Desk Ticketing System Installation!** 🎉 
  

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket Prereqs and Installation"/>
</p>
<p>

Click [here](https://github.com/jnoriega232/post-install-config) to move on to part 2 of this tutorial!
