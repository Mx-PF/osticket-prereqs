<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket Logo" width="300" />
</p>  

# osTicket Installation Guide  
### Build a Help Desk System Like a Pro  
This guide walks you through setting up **osTicket**, a free help desk system, on Windows 10 using Azure, IIS, PHP, and MySQL. Follow these simple steps to get started!

- ### Download the files [HERE](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) 📁

## Tools You’ll Need
- Windows 10 (Build 19044)
- Microsoft Azure (Virtual Machines)  
  [![Azure](https://img.shields.io/badge/Azure-VM-green?logo=microsoft-azure)](https://azure.microsoft.com)
- Remote Desktop (RDP)
- Internet Information Services (IIS)

## Prerequisites
- Set up a Virtual Machine in Azure
- Install osTicket v1.15.8
- Install HeidiSQL
- Install MySQL
- Install PHP
- Install Microsoft Visual C++ Redistributable

## Steps to Follow

### Step 1: Set Up a Virtual Machine in Azure
- **Create a Resource Group**  
  In Azure, make a new Resource Group.  
  <img src="https://i.imgur.com/1x9McoB.png" height="75%" width="100%" />

- **Create a Windows 10 VM**  
  Set up a Windows 10 VM with 2-4 Virtual CPUs. Choose a username and password (you’ll need them later to log in). Let Azure create a new Virtual Network (Vnet).  
  <img src="https://i.imgur.com/1D0ZTMx.png" height="75%" width="100%" />

- **Connect to Your VM**  
  Open Remote Desktop on your computer and log in to your VM using its public IP address.  
  <img src="https://imgur.com/Xnr6QVu.png" height="75%" width="100%" />

---

### Step 2: Turn On IIS in Windows
- Search for "Control Panel" on your VM.
- Go to "Programs" > "Turn Windows features on or off."
- Find "Internet Information Services (IIS)" and check the box.
- Expand "World Wide Web Services" > "Application Development Features" and check "CGI."  
  <img src="https://i.imgur.com/Xjp87s7.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/Sc2KNkM.png" height="75%" width="100%" />

---

### Step 3: Install PHP Manager
- Download and install PHP Manager. Accept all terms.  
  <img src="https://i.imgur.com/aFfUwvS.png" height="75%" width="100%" />

---

### Step 4: Install Rewrite Module
- Download and install the Rewrite Module. Accept all terms.  
  <img src="https://i.imgur.com/kfmvMUJ.png" height="75%" width="100%" />

---

### Step 5: Set Up a PHP Folder
- Open File Explorer and go to `C:\`.
- Create a new folder named `PHP`.
- Download `php-7.3.8-nts-Win32-VC15-x86.zip` from [HERE](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).
- Extract the zip file into `C:\PHP`.  
  <img src="https://i.imgur.com/HtAfBuK.png" height="75%" width="100%" />

---

### Step 6: Install Visual C++ Redistributable
- Download and install `VC_Redist`. Accept all terms.  
  <img src="https://i.imgur.com/FokLvyU.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/JfowAPC.png" height="75%" width="100%" />

---

### Step 7: Install MySQL
- Download and install MySQL. Accept all terms.
- Set a username and password (e.g., username: `root`, password: `Password1`).  
  <img src="https://i.imgur.com/IVpLg40.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/zdhWXNx.png" height="75%" width="100%" />

---

### Step 8: Install osTicket
- Download osTicket v1.15.8 from the link above.
- Extract the “upload” folder and copy it to `C:\inetpub\wwwroot`.
- Rename the “upload” folder to “osTicket”.  
  <img src="https://i.imgur.com/0MUJLMU.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/1h9goM8.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/pDikkgq.png" height="75%" width="100%" />

---

### Step 9: Restart IIS
- Open IIS Manager.
- Stop and start the server.  
  <img src="https://i.imgur.com/QeWNlG3.png" height="75%" width="100%" />

- In IIS, go to "Sites" > "Default Web Site" > "osTicket."
- Click "Browse *:80" to open osTicket in your browser.  
  <img src="https://i.imgur.com/3iXhNbi.png" height="75%" width="100%" />

---

### Step 10: Turn On PHP Extensions
- In IIS, go to "osTicket" and double-click "PHP Manager."
- Click "Enable or disable an extension."
- Enable: `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`.  
  <img src="https://i.imgur.com/LFKo5Hs.png" height="75%" width="100%" />  

- Refresh the osTicket site in your browser to see the updates.  
  <img src="https://i.imgur.com/6iSNd4H.png" height="75%" width="100%" />

---

### Step 11: Rename the Configuration File
- Go to `C:\inetpub\wwwroot\osTicket\include`.
- Rename `ost-sampleconfig.php` to `ost-config.php`.  
  <img src="https://i.imgur.com/TEw71SD.png" height="75%" width="100%" />

---

### Step 12: Set Permissions for `ost-config.php`
- Right-click `ost-config.php` > Properties > Security.
- Click "Edit" > "Remove" to disable inheritance.
- Add "Everyone" and give full control.  
  <img src="https://i.imgur.com/1QtRWEF.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/YzsMXNX.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/k7x9yGR.png" height="75%" width="100%" />

---

### Step 13: Set Up osTicket in the Browser
- Open the osTicket setup page in your browser.
- Enter a Helpdesk name and default email.
- Click "Continue" to move forward.  
  <img src="https://i.imgur.com/rvMvlNC.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/PtGCw26.png" height="75%" width="100%" />

---

### Step 14: Install HeidiSQL
- Download and install HeidiSQL.  
  <img src="https://i.imgur.com/AEg0b2P.png" height="75%" width="100%" />

- Open HeidiSQL and create a new session with username `root` and password `Password1`.
- Connect and create a database named `osTicket`.  
  <img src="https://i.imgur.com/9t51ApR.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/vXzmQqg.png" height="75%" width="100%" />

---

### Step 15: Finish osTicket Setup
- In the browser, enter these MySQL details:
  - Database: `osTicket`
  - Username: `root`
  - Password: `Password1`
- Click "Install Now!"  
  <img src="https://i.imgur.com/akDyber.png" height="75%" width="100%" />  
  <img src="https://i.imgur.com/J5omRoE.png" height="75%" width="100%" />

---

### Step 16: Clean Up
- Delete the `setup` folder in `C:\inetpub\wwwroot\osTicket`.  
  <img src="https://i.imgur.com/eg0ZPG3.png" height="75%" width="100%" />

- Set `ost-config.php` to "Read" only.  
  <img src="https://i.imgur.com/n6k46XL.png" height="75%" width="100%" />

---

### Step 17: Log In to osTicket
- Visit `http://localhost/osTicket/scp/login.php` and log in with your admin credentials.  
  <img src="https://i.imgur.com/8wvWH0H.jpg" height="75%" width="100%" />

---

### 🎉 Congratulations! You’ve Successfully Set Up osTicket! 🎊
