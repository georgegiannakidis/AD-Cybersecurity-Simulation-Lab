# AD-Cybersecurity-Simulation-Lab

## 🛡️ Overview

The **AD-Cybersecurity-Simulation-Lab** is a virtual cybersecurity lab that allows users to simulate both **red team** (attacks) and **blue team** (defense) activities. The lab uses **Active Directory**, **Splunk**, **Sysmon**, **Atomic Red Team**, and **Kali Linux** to create a real-world cybersecurity training environment.

## 🔑 Key Features
- **Red Team Simulations**: Attack simulations using Kali Linux and Atomic Red Team based on the MITRE ATT&CK framework.
- **Blue Team Monitoring**: Log monitoring with Splunk and Sysmon to detect and respond to attacks.
- **Active Directory (Windows Server 2022)**: A domain controller for user management and authentication.

## 🖥️ Network Setup
- **Domain**: `geo.global`
- **Devices**:
  - **Splunk Server**: `192.168.10.10`
  - **Windows 10 Client**: DHCP (Red/Blue team participant)
  - **Windows Server 2022**: `192.168.10.7` (Active Directory Domain Controller)
  - **Kali Linux**: `192.168.10.250` (Red team attack machine)

### Network Diagram
![Network Diagram](./assets/images/network-diagram.png)

## 🛠️ Tools and Technologies
- **Splunk**: Central log management.
- **Sysmon**: Detailed system monitoring.
- **Atomic Red Team**: Simulating adversary techniques.
- **Kali Linux**: Offensive security and penetration testing.

For more details, visit the [tools-used](./assets/docs/tools-used.md) file.

## ⚔️ Attack Simulations

### 1. Red Team Activity: Password Brute Force Attack
- **Tool**: Crowbar (Kali Linux)
- **Target**: Windows 10 Client
- **Outcome**: Successful brute force attack with user credentials for `Susan Smith`.

![Brute Force Log](./assets/images/crowbar-attack.png)

For more details, see [brute-force-attack.md](./assets/docs/brute-force-attack.md).

### 2. Blue Team Defense: Log Monitoring in Splunk
- **Splunk** captured multiple failed login attempts (Event ID 4625) and a successful login (Event ID 4624).
- The blue team investigated and identified the brute force attack through Splunk logs.

![Splunk Log Analysis](./assets/images/splunk-log-analysis.png)

For further information on attacks and defenses, see the [attack-description](./assets/docs/attack-description.md) file.

## 🚀 Lab Setup

### Requirements
- **Windows Server 2022** (for Active Directory)
- **Windows 10** (as a client machine)
- **Kali Linux** (as an attack machine)
- **Splunk Server** (log collection and monitoring)
- **Sysmon** (system logging for Windows)

### Quick Setup Guide
1. **Set Up Active Directory Domain Controller**:
   - Install **Windows Server 2022**.
   - Configure **Active Directory Domain Services (AD DS)**.
   - Follow the guide in [ad-setup-guide.md](./assets/docs/ad-setup-guide.md).
   
2. **Install Splunk Forwarders**:
   - Set up the **Splunk Universal Forwarder** on both the AD server and the Windows 10 client.

3. **Configure Sysmon**:
   - Install and configure **Sysmon** on both Windows machines with the provided configuration file.

4. **Run Atomic Red Team Attacks**:
   - Use **Atomic Red Team** to simulate various attack techniques like privilege escalation and account creation.

For a complete setup guide, visit the [setup-guide.md](./assets/docs/setup-guide.md) file.

## 🗂️ Project Structure

```plaintext
AD-Cybersecurity-Simulation-Lab/
│
├── README.md                      # Main project documentation
├── LICENSE                        # Project license
├── assets/
│   ├── images/                    # Images and screenshots
│   │   └── network-diagram.png    # Network diagram
│   │   └── splunk-log-analysis.png# Splunk log analysis screenshot
│   └── docs/                      # Documentation files
│       └── tools-used.md          # List of tools used
│       └── setup-guide.md         # Lab setup guide
│       └── attack-description.md  # Description of red/blue team activities
│       └── ad-setup-guide.md      # AD Domain Controller setup guide
│       └── brute-force-attack.md  # Detailed brute force attack description
└── configurations/
    └── sysmon-config.xml          # Sysmon configuration file
    └── splunk-forwarder.conf      # Splunk Universal Forwarder configuration
