<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration ( NOT READY YET)</h2>

- ### [YouTube: osTicket instalation](.)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 Pro</b> (22H2)

<h2>List of Prerequisites</h2>

- Azure account with permission to create VMs
- Basic knowledge of Windows
- Remote Desktop (RDP) access enabled
- Installation files in osTicket-Installation-Files.zip
- HTTP (port 80) and RDP (port 3389) open in the VM's firewall


<h2>Installation Steps</h2>

<h2>1 Step</h2>

![Step 1 Done](https://github.com/user-attachments/assets/e500b29a-4ec2-41f8-ac04-b396604c53b7)

<p>
Begin by creating a Windows 10 virtual machine in Azure with 4/2 vCPUs. Name the machine osticket-vm or whatever you wanna call it, set a username, and a password (tip: save it in a notepad). Once the VM is deployed, connect to it using Remote Desktop to begin the setup process.
</p>
<br />

<h2>2 Step</h2>

![Step 2](https://github.com/user-attachments/assets/d94fcfa4-1a1d-4986-bca5-5699f48ba933)


<p>
Inside the VM, download <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">the osTicket-Installation-Files.zip file</a> and extract it to the Desktop. This will create a folder called osTicket-Installation-Files, which contains all the necessary files for installing osTicket and its dependencies.
</p>
<br />

<h2>3 Step</h2>

![Step 3 Done](https://github.com/user-attachments/assets/82b0411b-8699-4958-bb6e-9c5a44260599)


<p>
Open the “Turn Windows features on or off” menu from the Control Panel. Enable Internet Information Services (IIS) and make sure to check CGI under World Wide Web Services > Application Development Features. This prepares the server for hosting the osTicket web application.
</p>
<br />

<h2>4 Step</h2>

![Step 4 Done](https://github.com/user-attachments/assets/9cad17ee-65ab-4223-af2f-ff51739b7ad7)


<p>
From the osTicket-Installation-Files folder, install PHP Manager for IIS and the Rewrite Module. Also install the VC++ Redistributable. Create the folder C:\PHP, then extract php-7.3.8-nts-Win32-VC15-x86.zip into it. Install MySQL 5.5.62 using the Typical Setup, then run the Configuration Wizard using Standard Configuration. Set the MySQL root username and password both to root.
</p>
<br />

<h2>5 Step</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Launch IIS Manager as Administrator (windows key and type IIS). In PHP Manager, register the PHP executable located at C:\PHP\php-cgi.exe. Stop and start the IIS server to apply the changes. Extract the osTicket-v1.15.8.zip file and copy the upload folder into C:\inetpub\wwwroot, renaming it to osTicket. Restart IIS again. In IIS Manager, navigate to the Default Web Site (over the left side), select osTicket and double click PHP Manager, enable the following PHP extensions: php_imap.dll, php_intl.dll, and php_opcache.dll. Then click “Browse *:80” to open the site.
</p>
<br />

<h2>6 Step</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Navigate to the folder C:\inetpub\wwwroot\osTicket\include and rename ost-sampleconfig.php to ost-config.php. Right-click the file, go to Properties > Security, disable inheritance, remove all existing permissions, and add new full control permissions for Everyone. Go back to the osTicket browser setup page, enter with a Helpdesk name and default support email address (made up) to continue.
</p>
<br />

<h2>7 Step</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install HeidiSQL from the installation files. Launch HeidiSQL, create a new session using the username root and password root, and connect. Create a new database called osTicket. Return to the osTicket setup page in the browser, enter the database name osTicket, username root, and password root, then click “Install Now!” Once the installation is complete, access the admin login page at http://localhost/osTicket/scp/login.php and the end-user portal at http://localhost/osTicket/. Finally, delete the C:\inetpub\wwwroot\osTicket\setup folder and set the ost-config.php file to read-only.
</p>
<br />
