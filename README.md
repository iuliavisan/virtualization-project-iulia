# Virtualization Project – Windows & Linux Network Setup

This project was developed as part of a university assignment to simulate a small IT infrastructure using three virtual machines. Each machine was configured with specific roles and services, with a focus on understanding how systems communicate in a local network environment. Everything was done manually, step by step, without using automation or templates. Every step can be visually seen and tracked through the related directories(screenshots).

## Project Requirements

This virtualization project was based on specifications provided by the course instructor. The goal was to simulate a small virtualized network using three virtual machines, each with specific roles and services.

You may use **any virtualization tool** (VMware, VirtualBox, Hyper-V, etc.).

### VM1 – Windows Client Machine
- Operating system: Windows 10/11 Pro, XP Pro, 8, etc.
- Must be joined to a domain.
- Install `putty.exe` and `WinSCP.exe`.
- Host a basic web server with a simple HTML page showing:
  - Message: `"Hello Windows 10 Pro"`  
  - Your name
- Enable and configure Windows Firewall.

---

### VM2 – Windows Server
- OS: Windows Server 2016 (or 2019, 2022, 2008, etc.)
- Set up as a **Domain Controller**.
- Configure **Active Directory**:
  - Create group `Professors`
    - Users: `sebi`, `sergiu`
  - Create group `Students`
    - Users: `stud1`, `stud2`
- Set up **DNS Server**
  - Forward and Reverse Lookup Zones
- Set up **Web Server (IIS)** with **two distinct websites**:
  - e.g. `student.ro`, `profesor.com`  
  - Each should contain your name in the content
- Configure **File Server** with the following:
  - `Professors` folder:
    - Full access for Professors
    - Read-only access for Students
  - `Students` folder:
    - Full access for both Students and Professors
- Configure optional **Certificate Authority (CA)** to allow HTTPS access to websites (optional).
- Set up **Group Policy Objects (GPO)**:
  - For `sergiu`: restrict Task Manager access
  - For `sebi`: password history set to 21 days, expiration at 30 days, minimum length = 10 characters

---

### VM3 – Linux Server
- OS: Any Linux distribution (Ubuntu, Fedora, etc.)
- Set up **Mail Server** (e.g. Postfix, Sendmail, or another mail agent)
  - Minimum of 2 users
- Configure **Web Server** (Apache or Nginx) with two virtual hosts:
  - `site1`
  - `site2`
- Install and configure **SSH** (must allow remote access to the machine)
- Set up **File Server** using Samba:
  - `Folder1`: read-only
  - `Folder2`: write access
- Install and configure **Firewall**
- Install and configure **FTP Server**
- (Optional) Configure a **Certificate Authority** to enable HTTPS

---

### Network Requirements

All machines must be on the **same network** (e.g. NAT or Bridged), to ensure proper communication between them.


#

The first machine runs Windows 10 Pro. It was configured as a client that joins a domain created on the second machine. I assigned it a static IP address, set the preferred DNS to the server’s IP, and tested its connection to internal websites hosted locally. I also installed PuTTY and WinSCP for remote access and file transfer, and configured the firewall to allow specific ports and applications. Additionally, I used the hosts file to simulate domain resolution for custom hostnames like `profesor.com` and `student.ro`.

The second machine is a Windows Server 2016 system set up as a domain controller using Active Directory Domain Services. I also installed the DNS role and created forward lookup zones to resolve domain names used within the network. Internet Information Services (IIS) was used to host two separate websites, each with its own hostname and binding configuration. I configured file sharing by creating folders with specific permissions for different user groups. Group Policy Objects (GPOs) were applied to individual users for customization and restrictions (e.g., disabling access to certain features or redirecting folders). I also explored optional configuration for a Certificate Authority.

The third machine runs Lubuntu, a lightweight Linux distribution, to save resources. This machine includes several services configured manually via terminal. I installed and set up Postfix and Dovecot to create a basic mail server with at least two users, and used Thunderbird as a mail client for testing. I configured Apache2 to host two different websites using VirtualHosts and mapped them to the client through the hosts file. I enabled and tested SSH access, set up Samba to share folders between Linux and Windows, and configured an FTP server using vsftpd. The firewall was also configured using `ufw` to allow or deny specific traffic. All these services were installed, tested, and documented step by step.

All documentation is written in Romanian and included in `.txt` format. The IP addresses used throughout the project are from a local private network (192.168.x.x range) and were used strictly in a controlled test environment.

This project gave me practical experience in setting up and managing both Windows and Linux systems, configuring services, dealing with IP addressing and DNS, and understanding how different operating systems interact on the same network. It also improved my troubleshooting skills and my ability to configure services without relying on pre-built solutions.

Visual documentation is present in each correspondent directory.

