# Active Directory Setup Guide

In this guide, I’ll show you how I set up **Active Directory** on **Windows Server 2022** in my **AD-Cybersecurity-Simulation-Lab**.

## 🛠️ Step 1: Install Active Directory Domain Services (AD DS)

### 1.1 Install Windows Server 2022
First, I installed **Windows Server 2022** on a virtual machine and assigned it a static IP address of `192.168.10.7`. This machine will act as the domain controller for the lab.

### 1.2 Adding the AD DS Role
In **Server Manager**, I clicked **Add roles and features** and selected **Active Directory Domain Services (AD DS)**. After installation, I promoted the server to a domain controller.

### 1.3 Configuring the Domain
While promoting the server, I set the domain name to `geo.global`. Once the wizard completed, I let the server reboot to apply all the changes.

## 🖥️ Step 2: Create Organizational Units and Users

### 2.1 Setting Up OUs
In **Active Directory Users and Computers**, I created two Organizational Units (OUs):
1. **IT**
2. **HR**

### 2.2 Adding Users
Next, I added two users:
- **John Doe** under the IT OU.
- **Susan Smith** under the HR OU.

## 🎯 Conclusion
With this setup, I now had a fully functional Active Directory Domain Controller to manage users, policies, and security across my lab environment.
