# Virtualization Project – Windows & Linux Network Setup

This project was developed as part of a university assignment to simulate a small IT infrastructure using three virtual machines. Each machine was configured with specific roles and services, with a focus on understanding how systems communicate in a local network environment. Everything was done manually, step by step, without using automation or templates.

The first machine runs Windows 10 Pro. It was configured as a client that joins a domain created on the second machine. I assigned it a static IP address, set the preferred DNS to the server’s IP, and tested its connection to internal websites hosted locally. I also installed PuTTY and WinSCP for remote access and file transfer, and configured the firewall to allow specific ports and applications. Additionally, I used the hosts file to simulate domain resolution for custom hostnames like `profesor.com` and `student.ro`.

The second machine is a Windows Server 2016 system set up as a domain controller using Active Directory Domain Services. I also installed the DNS role and created forward lookup zones to resolve domain names used within the network. Internet Information Services (IIS) was used to host two separate websites, each with its own hostname and binding configuration. I configured file sharing by creating folders with specific permissions for different user groups. Group Policy Objects (GPOs) were applied to individual users for customization and restrictions (e.g., disabling access to certain features or redirecting folders). I also explored optional configuration for a Certificate Authority.

The third machine runs Lubuntu, a lightweight Linux distribution, to save resources. This machine includes several services configured manually via terminal. I installed and set up Postfix and Dovecot to create a basic mail server with at least two users, and used Thunderbird as a mail client for testing. I configured Apache2 to host two different websites using VirtualHosts and mapped them to the client through the hosts file. I enabled and tested SSH access, set up Samba to share folders between Linux and Windows, and configured an FTP server using vsftpd. The firewall was also configured using `ufw` to allow or deny specific traffic. All these services were installed, tested, and documented step by step.

All documentation is written in Romanian and included in `.txt` format. The IP addresses used throughout the project are from a local private network (192.168.x.x range) and were used strictly in a controlled test environment.

This project gave me practical experience in setting up and managing both Windows and Linux systems, configuring services, dealing with IP addressing and DNS, and understanding how different operating systems interact on the same network. It also improved my troubleshooting skills and my ability to configure services without relying on pre-built solutions.

I plan to extend this project by adding screenshots.

