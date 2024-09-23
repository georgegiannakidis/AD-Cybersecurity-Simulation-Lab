# AD-Cybersecurity-Simulation-Lab

## Overview
The **AD-Cybersecurity-Simulation-Lab** is a controlled lab environment designed to simulate and monitor cybersecurity attacks using a combination of **Active Directory**, **Splunk**, **Sysmon**, **Atomic Red Team**, and **Kali Linux**. The lab is structured to demonstrate both **red team** (offensive) and **blue team** (defensive) activities, providing a real-world scenario for improving threat detection and response skills.

## Key Features
- **Red Team Simulations**: Simulate various attack techniques using Kali Linux and Atomic Red Team, based on the MITRE ATT&CK framework.
- **Blue Team Monitoring**: Capture and analyze system logs with **Splunk** and **Sysmon** to detect, investigate, and mitigate attacks.
- **Active Directory**: The lab uses **Windows Server 2022** as the Active Directory Domain Controller (ADDC), which manages user authentication, policies, and system security.
  
## Network Setup
- **Domain**: geo.global
- **Subnet**: 192.168.10.0/24
- **Devices**:
  - **Splunk Server**: IP 192.168.10.10 (Collects and visualizes logs from all network devices)
  - **Windows 10 Client**: Uses DHCP (participates in red and blue team activities)
  - **Windows Server 2022 (Active Directory Domain Controller)**: IP 192.168.10.7 (Manages domain users and policies)
  - **Kali Linux (Attacker)**: IP 192.168.10.250 (Used for red team penetration testing)
  
### Network Diagram
![Network Diagram](./images/network-diagram.png)

## Tools and Technologies
- **Splunk**: Centralized log management and analysis.
- **Sysmon**: Windows system monitoring for detailed logging of processes and activities.
- **Atomic Red Team**: A tool for simulating adversary techniques based on MITRE ATT&CK.
- **Crowbar (Kali Linux)**: A brute force tool used for password attack simulations.

For a detailed list and descriptions of the tools used, visit the [tools-used.md](./docs/tools-used.md) file.

## Attack Simulations
### 1. Red Team Activity: Password Brute Force Attack
- **Crowbar Tool** (Kali Linux) was used to perform a brute force attack on the **Windows 10 machine** using a dictionary of passwords.
- The attack was successful with user Susan Smith’s password: `wH0ish1r!nG`.
  
![Brute Force Log](./images/crowbar-attack.png)

More information about the brute force attack can be found in [brute-force-attack.md](./attacks/brute-force-attack.md).

### 2. Blue Team Defense: Log Monitoring with Splunk
- Splunk captured logs showing multiple failed login attempts (Event ID 4625) and one successful login (Event ID 4624), signaling a brute force attack.
- Blue team investigators can filter and analyze these logs to detect and respond to the attack.

![Splunk Log Analysis](./images/splunk-log-analysis.png)

### 3. Atomic Red Team Simulation: Account Creation Attack
- Used **Atomic Red Team** to simulate an account creation attack (MITRE ATT&CK T1136.001) on the domain controller.
- Created a new local admin user `NewLocalUser` via PowerShell.

![New Local User](./images/new-local-user.png)

For more details about the red and blue team activities, visit [attack-description.md](./docs/attack-description.md).

## Setting Up the Lab
### Requirements
- **Windows Server 2022** for Active Directory
- **Windows 10** as a client machine
- **Kali Linux** as the attack machine
- **Splunk Server** for log collection and monitoring
- **Sysmon** for detailed Windows event logging

### Installation and Configuration
1. **Active Directory Domain Controller Setup**:
   - Install **Windows Server 2022**.
   - Add the **Active Directory Domain Services (AD DS)** role and promote the server to a domain controller.
   - Create the domain `geo.global` and set up organizational units (IT, HR), adding users (`John Doe`, `Susan Smith`).
   
   Follow the detailed guide in [ad-setup-guide.md](./configurations/ad-setup-guide.md).

2. **Splunk Universal Forwarder**:
   - Install the **Splunk Universal Forwarder** on the Active Directory server and Windows 10 client.
   - Forward system logs to the Splunk server (192.168.10.10).

3. **Sysmon Configuration**:
   - Install **Sysmon** on the Active Directory and Windows 10 machines.
   - Use the provided configuration file (`sysmon-config.xml`) for detailed system logging.

4. **Atomic Red Team Setup**:
   - Install **Atomic Red Team** on the Windows 10 machine to simulate various attack techniques.
   - Run simulations such as account creation and privilege escalation for blue team detection tests.

For a full setup guide, visit [setup-guide.md](./docs/setup-guide.md).

### Configuration Files
All relevant configuration files, including Splunk and Sysmon settings, can be found in the `configurations/` folder.

## Usage
1. Set up all the virtual machines and configure networking as per the network diagram.
2. Install and configure all the tools (Splunk, Sysmon, Atomic Red Team) as described in the setup guide.
3. Simulate attacks using Kali Linux or Atomic Red Team, and monitor security logs using Splunk.
4. Investigate and mitigate the simulated attacks from the blue team perspective.

## Screenshots
![VMs Running](./images/vms-running.png)

## Conclusion
This project demonstrates the integration of **Active Directory**, **Splunk**, **Sysmon**, and **Kali Linux** to create a comprehensive cybersecurity simulation lab. The lab allows participants to practice both attacking and defending within a real-world environment, sharpening their skills in threat detection, response, and mitigation.

## Folder Structure
- `docs/`: Contains network diagrams, attack descriptions, and setup guides.
- `images/`: Contains screenshots and visual documentation.
- `scripts/`: Contains PowerShell scripts and configuration files.
- `configurations/`: Contains configuration files for Splunk, Sysmon, etc.
- `attacks/`: Descriptions of attack scenarios and techniques simulated in the lab.
