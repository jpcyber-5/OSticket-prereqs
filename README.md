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


![Screenshot 2025-05-27 195500](https://github.com/user-attachments/assets/e0ad6507-5472-41d2-a019-ae8b5c141aa4)


---
### 4. Enable IIS & CGI
- Enable IIS in Windows Features:
  - World Wide Web Services → Application Development Features → ✔️ CGI
 ![Screenshot 2025-05-27 195757](https://github.com/user-attachments/assets/9571b357-8a3f-48cc-8c6f-e52340cc9b8f)

---

### 5. Install Required Tools
From the `osTicket-Installation-Files` folder:
- Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`)
- Install **URL Rewrite Module** (`rewrite_amd64_en-US.msi`)
- Install **VC_redist.x86.exe`

  
![Screenshot 2025-05-27 200038](https://github.com/user-attachments/assets/4f6e7ab6-9ada-44d3-b562-de7dd3bfd322)
![Screenshot 2025-05-27 200120](https://github.com/user-attachments/assets/46315d9c-1ffa-45dc-8ea8-52d60684a2b9)
![Screenshot 2025-05-27 200449](https://github.com/user-attachments/assets/254eafa2-3cab-4a5e-9c1a-13b1dc1885d1)



---

### 6. Setup PHP
- Create folder: `C:\PHP`
- Extract `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`
- Register `php-cgi.exe` via **PHP Manager** in IIS
- Restart IIS (Stop/Start server)

![Screenshot 2025-05-27 200408](https://github.com/user-attachments/assets/1daddcd5-de19-415c-b3db-57ca558db9ee)

![Screenshot 2025-05-27 201546](https://github.com/user-attachments/assets/c319d3e6-339d-48e7-9fd3-ea03b3195a17)
![Screenshot 2025-05-27 201601](https://github.com/user-attachments/assets/bdb8fe08-c359-463d-8699-6325d0f6091d)
![Screenshot 2025-05-27 201624](https://github.com/user-attachments/assets/751d2744-d01a-469a-b17d-b7b0b7ff0f53)
![Screenshot 2025-05-27 201633](https://github.com/user-attachments/assets/b13518b4-ba52-47ed-8bb5-87fe1f6f4479)

---

### 7. Install MySQL
- Install `mysql-5.5.62-win32.msi` (Typical Setup)
- Run Configuration Wizard → Standard Configuration
  - Username: `root`
  - Password: `root`
 

![Screenshot 2025-05-27 200743](https://github.com/user-attachments/assets/0176ea6f-3699-4be0-a8dc-41244993f010)
![Screenshot 2025-05-27 200819](https://github.com/user-attachments/assets/1168f71b-4bdf-49cb-8d27-9b47cb10785a)


---

### 8. Install osTicket
- Extract `osTicket-v1.15.8.zip`
- Copy `upload` folder to `C:\inetpub\wwwroot`
- Rename `upload` to `osTicket`
- Restart IIS

  
![Screenshot 2025-05-27 202551](https://github.com/user-attachments/assets/2e18aa38-789d-4891-83db-596fcb2058db)
![Screenshot 2025-05-27 202601](https://github.com/user-attachments/assets/be43142d-9ada-43ae-b664-f0181d7a3cdb)
![Screenshot 2025-05-27 202731](https://github.com/user-attachments/assets/bb29edbf-7a3d-42e8-92a9-264fe4f0b161)


---
### 9. Browse to osTicket
- In IIS: Sites → Default Web Site → osTicket
- Click “Browse *:80”
- Note any missing PHP extensions

![Screenshot 2025-05-27 202827](https://github.com/user-attachments/assets/909f7d01-842b-49c4-af7d-567c987b7b3b)
![Screenshot 2025-05-27 202834](https://github.com/user-attachments/assets/2fc11d8d-99b5-4925-9994-6a9cdea23dc0)
![Screenshot 2025-05-27 202853](https://github.com/user-attachments/assets/653b1590-2014-4f5f-ad5c-2a24d64fbf3d)

---
### 10. Enable PHP Extensions
In PHP Manager (IIS):
- Enable:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
- Refresh browser
![Screenshot 2025-05-27 203321](https://github.com/user-attachments/assets/7545c611-d339-4fbd-808a-3d3405ca0a0f)

![Screenshot 2025-05-27 203336](https://github.com/user-attachments/assets/d5b9f4f0-394a-4256-a708-9337ee69903a)

---
### 11. Configure osTicket
- Rename:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `ost-config.php`
- Set Permissions:
  - Disable inheritance
  - Remove all existing permissions
  - Add `Everyone` → Full Control
 
  
![Screenshot 2025-05-27 203652](https://github.com/user-attachments/assets/255b1541-eab0-45f8-a152-4c528e2ce94c)
![Screenshot 2025-05-27 203723](https://github.com/user-attachments/assets/c3e74d52-4a45-4716-89b7-0f6b950b02e2)
![Screenshot 2025-05-27 203806](https://github.com/user-attachments/assets/0ba6a5ec-5251-4467-a018-e546a43a7f7d)
![Screenshot 2025-05-27 204257](https://github.com/user-attachments/assets/0daf2708-cbc0-425a-b0b8-2af4d0688cb7)


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
