# Born2BeRoot
This 42 School's Born2BeRoot Project Guide was made using information obtained from several other similar guides and sources in order to better prepare my defence of this project. The questions answered below were obtained from [this document](https://docs.google.com/document/d/1-BwCO0udUP7MhRh81Y681zz0BalXtKFtte_FHJc6G4s/edit) (by Adrian Musso-Gonzalez) and answered in both english and portuguese.

In order to really grasp the information needed for this project, I recommend writing your own guide (feel free to use this one as a starting point to make your own). 
## Index
I. [English Guide](#english-guide)
 - [What is a Virtual Machine?](#what-is-a-virtual-machine)
 - [How does a Virtual Machine work and what is its purpose?](#how-does-a-virtual-machine-work-and-what-is-its-purpose)
 - [*Debian* vs *Rocky Linux*](#debian-vs-rocky-linux)
 - [What's the difference between aptitude and apt?](#whats-the-difference-between-aptitude-and-apt)
 - [What is AppArmor?](#what-is-apparmor)
 - [Password policy and rules](#password-policy-and-rules)
 - [What is LVM?](#what-is-lvm)
 - [Uncomplicated Firewall (UFW)](#uncomplicated-firewall-ufw)
 - [SSH - How it works and what it means](#ssh---how-it-works-and-what-it-means)
 - [What is Cron?](#what-is-cron)
 
 II. [Portuguese Guide](#portuguese-guide)
 
III. [Sources and Further Reading](#sources-and-further-reading)

## English Guide

### What is a Virtual Machine?

A Virtual Machine (VM) is an application that utilises software instead of a physical device to run programs and launch applications. It is hosted on a physical computer and allows the installation of an Operating System (OS) into it, running the OS as if it were installed on the physical computer directly. This allows, amongst other things, to test applications in a safe, separate environment.

### How does a Virtual Machine work and what is its purpose?

Virtual Machines act as virtual devices that behave as physical devices - they utilise their own CPU, RAM, storage and network interface (this is possible because the VM is hosted on a physical machine). The software responsible for creating VMs and for isolating hardware resources (hardware virtualisation) for them to use is called **hypervisor**. This software is also responsible for implementing all necessary changes to allow the utilisation of those resources by VMs. 

![Hardware Virtualisation by MongoDB](https://webimages.mongodb.com/_com_assets/cms/lh54zev0ad49yc8uj-vm2.jpg?auto=format%252Ccompress)
Image source:  [A Guide to Virtual Machines (VM) by MongoDB](https://www.mongodb.com/cloud-explained/virtual-machines) 

### *Debian* vs *Rocky Linux*
Both *Debian* and *Rocky* are Linux distributions even though they are distinct in many ways. 

 - *Debian* is [upstream](https://reflectoring.io/upstream-downstream/) of Ubuntu and uses the same package format and package manager as it does, **.deb** and **apt** respectively. It's a distribution known for having many software packages available and for supporting several system architectures.
 
 - *Rocky Linux* is a community enterprise downstream of RHEL (Red Hat Enterprise Linux) introduced as an alternative to the former CentOS. It uses a **.rpm** package format and **yum** as package manager. It is a stable distribution with regular security patches.
 
### What's the difference between aptitude and APT?
Advanced Packaging Tool (APT) is a package management system designed for *Debian* for the **dpkg** utility. It is used to install or upgrade all dependencies so that **.deb** packages can be installed. It is a lower-level package manager and is restricted to command line only.

Aptitude is front-end to APT, adding a user interface to the functionality allowing the user to interactively search for a package and install/remove it.

All in all, Aptitude is a high-level package manager while APT is a low-level package manager which can be used by other high-level package managers. Aptitude has more functionalities than APT while integrating the functionality of APT.
 
### What is AppArmor?
AppArmor is a Linux application security system that provides Mandatory Access Control (MAC) security. It allows system admin to restrict the actions that processes can perform. AppArmor confinement is provided by profiles, which can work in complain-more (AppArmor prohibits applications from performing restricted tasks) or in enforce-mode (AppArmor allows applications to do restricted tasks, but creates a registry entry to display the complaint).
### Password policy and rules
As said by Pasquale Rossi in his [guide](https://github.com/pasqualerossi/Born2BeRoot-Guide#password-rules):
>For the password rules, we use the password quality checking library and there are two files the common-password file which sets the rules like upper and lower case characters, duplicate characters etc and the login.defs file which stores the password expiration rules (30 days etc). Sudo nano /etc/login.defs Sudo nano /etc/pam.d/common-password

### What is LVM?
LVM stands for Logical Volume Manager. It is an abstraction layer between a storage device and a file system that allows flexibility when managing partitions. This permits expanding the storage of partitions (logical volumes) without worrying about the contiguous space available on each logical volume and allows moving different logical volumes between physical devices.

### Uncomplicated Firewall (UFW)

### SSH - How it works and what it means
SSH or Secure Shell is a network communication protocol that enables secure system administration and file transfers over insecure networks. It works by encrypting the secure connection between a client and a server. As said in the [SSH website](https://www.ssh.com/academy/ssh/protocol):
 > The protocol works in the client-server model, which means that the connection is established by the SSH client connecting to the SSH server. The SSH client drives the connection setup process and uses public key cryptography to verify the identity of the SSH server. After the setup phase the SSH protocol uses strong symmetric encryption and hashing algorithms to ensure the privacy and integrity of the data that is exchanged between the client and server.
 
![Simplified setup flow of a secure shell connection by SSH Academy](https://www.ssh.com/hs-fs/hubfs/SSH_Client_Server.png?width=1112&name=SSH_Client_Server.png)
Image source:  [Simplified setup flow of a secure shell connection by SSH Academy](https://www.ssh.com/academy/ssh/protocol) 

Above are mentioned two different encryption techniques - symmetric encryption and hashing.
#### Symmetric Encryption
This technique encompasses utilising a solitary key to encode the data being sent and the same key to decode this data at its objective. For this reason, this method is also referred to as *shared key encryption*. 
A common issue with this kind of trade is the underlying key trade. In the event that an outside figure manages to access the trade during this stage, they would be able to acquire the key and decrypt the data.

![Symmetric Encryption by Wallarm](https://assets.website-files.com/5ff66329429d880392f6cba2/61c1b8f7eacaeb13c258c3c8_Symmetrical%20Encryption.png)Image source:  [Symmetric Encryption by Wallarm](https://www.wallarm.com/what/what-is-ssh-protocol) 

#### Hashing
Hashing is a technique that transforms data value into another value for the purpose of security. Hashing is used as one-way encryption and hashed values are very had to decode. It can be used in password validation, blockchain and message/fie integrity in order to prevent interference or tampering of information.

![enter image description here](https://assets.website-files.com/5ff66329429d880392f6cba2/61c1b9202cf1ace217ea77b7_Hashing.png)Image source:  [Hashing Algorithms by Wallarm](https://www.wallarm.com/what/what-is-ssh-protocol) 

### What is Cron?
 The cron standard Unix utility can be used to schedule commands or scripts for automatic execution at specific intervals (for instance, at a specific time of day).
 
## Portuguese Guide

## Sources and Further Reading

- [How to Choose a Linux Distribution](https://www.digitalocean.com/community/conceptual-articles/how-to-choose-a-linux-distribution)
(consulted on 8th May 2023)

- [Advanced Packaging Tool (APT)](https://geek-university.com/advanced-packaging-tool-apt/)
(consulted on 8th May 2023)

- [What is APT and Aptitude? and What’s real Difference Between Them?](https://www.tecmint.com/difference-between-apt-and-aptitude/)
(consulted on 8th May 2023)

- [Package Management Essentials: apt, yum, dnf, pkg](https://www.digitalocean.com/community/tutorials/package-management-basics-apt-yum-dnf-pkg)
(consulted on 8th May 2023)

- [Debian 11 vs Debian 10 vs Rocky Linux 8](https://computingforgeeks.com/debian-11-vs-debian-10-vs-rocky-linux-8-comparison-table/?utm_content=cmp-true)
(consulted on 8th May 2023)

- [What is Rocky Linux?](https://operavps.com/what-is-rocky-linux/)
(consulted on 8th May 2023)

- [Pasquale Rossi's Born2BeRoot Guide](https://github.com/pasqualerossi/Born2BeRoot-Guide)
(consulted on 8th May 2023)

- [Ayoub's Born2BeRoot Repository](https://github.com/ayoub0x1/born2beroot#introduction)
(consulted on 8th May 2023)

- [AppArmor - Ubuntu Wiki](https://wiki.ubuntu.com/AppArmor)
(consulted on 8th May 2023)

- [AppArmor](https://apparmor.net/)
(consulted on 8th May 2023)

- [What is SSH (Secure Shell)?](https://www.ssh.com/academy/ssh)
(consulted on 9th May 2023)

- [What is SSH Protocol?](https://www.wallarm.com/what/what-is-ssh-protocol)
(consulted on 9th May 2023)

- [What is Cron and How do I Use it?](https://www.pair.com/support/kb/configuring-cron/)
(consulted on 9th May 2023)
