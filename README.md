<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation

This tutorial outlines the prerequisites and step-by-step installation of the open-source help desk ticketing system **osTicket**, configured on a Windows 10 Virtual Machine hosted in Microsoft Azure.


---

## 💻 Environments and Technologies Used
- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- MySQL 5.5.62
- PHP 7.3.8
- HeidiSQL
- Windows 10 Pro (21H2)

---

## 🖥️ Operating System Used
- Windows 10 Pro (21H2)

---

## ✅ List of Prerequisites
1. Azure Virtual Machine (Windows 10, 2 vCPUs)
2. Remote Desktop Access
3. IIS with CGI and Application Development Features
4. PHP Manager, URL Rewrite Module, PHP 7.3.8
5. Visual C++ Redistributable
6. MySQL 5.5.62 and HeidiSQL
7. osTicket v1.15.8 Installation Files

---

## ⚙️ Installation Steps
---
### 1. Create Virtual Machine
- Name: `osticket-vm`
- OS: Windows 10
- Specs: 2 vCPUs, 16GB RAM
- Username: `labuser`
- Password: `osTicketPassword1!`
![Screenshot 2025-05-27 194107](https://github.com/user-attachments/assets/19e676f5-5adf-485e-9d88-5eb8f9a7576f)

---
### 2. Remote Desktop Login
- Log into the VM using Remote Desktop with the above credentials.

![Screenshot 2025-05-27 194750](https://github.com/user-attachments/assets/c0a993e6-fd13-4729-9d1e-d3256d5506ee)

![Screenshot 2025-05-27 194859](https://github.com/user-attachments/assets/6ed962ac-9644-459e-99e3-d3d26b5f23c9)

---
### 3. Extract Installation Files
- Download and extract `osTicket-Installation-Files.zip` to your Desktop.
- Folder should be named: `osTicket-Installation-Files`.


---
### 4. Enable IIS & CGI
- Enable IIS in Windows Features:
  - World Wide Web Services → Application Development Features → ✔️ CGI
 
---

### 5. Install Required Tools
From the `osTicket-Installation-Files` folder:
- Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`)
- Install **URL Rewrite Module** (`rewrite_amd64_en-US.msi`)
- Install **VC_redist.x86.exe`

---

### 6. Setup PHP
- Create folder: `C:\PHP`
- Extract `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`
- Register `php-cgi.exe` via **PHP Manager** in IIS
- Restart IIS (Stop/Start server)


---

### 7. Install MySQL
- Install `mysql-5.5.62-win32.msi` (Typical Setup)
- Run Configuration Wizard → Standard Configuration
  - Username: `root`
  - Password: `root`


---

### 8. Install osTicket
- Extract `osTicket-v1.15.8.zip`
- Copy `upload` folder to `C:\inetpub\wwwroot`
- Rename `upload` to `osTicket`
- Restart IIS


---
### 9. Browse to osTicket
- In IIS: Sites → Default Web Site → osTicket
- Click “Browse *:80”
- Note any missing PHP extensions


---
### 10. Enable PHP Extensions
In PHP Manager (IIS):
- Enable:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
- Refresh browser


---
### 11. Configure osTicket
- Rename:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `ost-config.php`
- Set Permissions:
  - Disable inheritance
  - Remove all existing permissions
  - Add `Everyone` → Full Control

---
### 12. Setup Database
- Install and open **HeidiSQL**
- Connect using:
  - Username: `root`
  - Password: `root`
- Create new database: `osTicket`


---
### 13. Complete Installation via Browser
- Provide Helpdesk name and default email
- Database:
  - Name: `osTicket`
  - Username: `root`
  - Password: `root`
- Click **Install Now!**
- Confirm installation:
  - Admin Login: `http://localhost/osTicket/scp/login.php`
  - User Portal: `http://localhost/osTicket/`

---

## 🧹 Post-Installation Cleanup
- Delete: `C:\inetpub\wwwroot\osTicket\setup`
- Set Read-only permissions on: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

---

## ✅ Status
- osTicket successfully installed and operational on local server.
