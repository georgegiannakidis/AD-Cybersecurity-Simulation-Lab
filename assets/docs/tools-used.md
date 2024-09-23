# Tools I Used in AD-Cybersecurity-Simulation-Lab

This document details the key tools I used to build and operate the **AD-Cybersecurity-Simulation-Lab**. Each tool plays a vital role in either simulating attacks or monitoring the network for security events.

## 🔍 1. **Splunk**
- **Category**: Log Management and SIEM
- **What I did**: I set up **Splunk** as the primary log management tool in the lab. I installed it on a dedicated server and configured it to collect logs from my **Windows Server 2022** (Active Directory) and **Windows 10** client. 
- **How I used it**: Splunk helped me centralize all system logs and create dashboards to monitor red team activities. For example, when I ran a brute force attack, I used Splunk to detect failed login attempts and successful logins via specific **event IDs** (like 4625 and 4624).
- **Purpose**: This allowed me to analyze real-time data and set up alerts for suspicious activities.
- **Website**: [Splunk Official Site](https://www.splunk.com)

---

## 🛡️ 2. **Sysmon (System Monitor)**
- **Category**: System Monitoring
- **What I did**: I installed **Sysmon** on both the **Windows Server 2022 (Active Directory)** and the **Windows 10 client**. Sysmon was crucial in providing detailed logs about system activity, including process creation, network connections, and file modifications.
- **How I used it**: With Sysmon forwarding logs to Splunk, I was able to detect suspicious events during attack simulations, such as unauthorized account creation and suspicious PowerShell commands.
- **Purpose**: It allowed me to get granular insights into system activity, helping the **blue team** detect any malicious actions.
- **Website**: [Sysmon Official Page](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)

---

## 🔨 3. **Atomic Red Team**
- **Category**: Attack Simulation
- **What I did**: I used **Atomic Red Team** on the **Windows 10 client** to simulate various attack techniques, following the **MITRE ATT&CK** framework. For instance, I tested the **T1136.001 (Create Account)** technique to simulate the creation of a rogue admin account.
- **How I used it**: After running the attack, I switched over to **Splunk** to confirm that the simulated attack was logged properly, and I verified that the blue team could detect the attack using event logs.
- **Purpose**: I used it to practice real-world attack scenarios, giving me the chance to test detection capabilities and improve defensive responses.
- **Website**: [Atomic Red Team GitHub](https://github.com/redcanaryco/atomic-red-team)

---

## 💻 4. **Kali Linux**
- **Category**: Penetration Testing and Offensive Security
- **What I did**: I set up **Kali Linux** as the dedicated attack machine in my lab environment. From Kali, I conducted multiple red team exercises, including password brute force attacks.
- **How I used it**: I used **Crowbar**, a brute force tool in Kali, to try and crack user credentials on the **Windows 10 client**. I successfully gained access to the user account `Susan Smith` using her password `wH0ish1r!nG`.
- **Purpose**: Kali Linux gave me all the offensive security tools I needed to simulate real-world attacks and test how well my defenses held up.
- **Website**: [Kali Linux Official Site](https://www.kali.org)

---

## 🔑 5. **Crowbar (Kali Linux Tool)**
- **Category**: Password Brute Force Tool
- **What I did**: Using **Crowbar** from the Kali Linux machine, I carried out a brute force password attack against the **Windows 10 client**.
- **How I used it**: I selected a small password dictionary and used Crowbar to test multiple password attempts for the user `Susan Smith`. After several failed attempts, I successfully cracked the password (`wH0ish1r!nG`), gaining unauthorized access.
- **Purpose**: This tool allowed me to test the security strength of my user credentials and observe how these attempts were logged in Splunk for detection.
- **Website**: [Crowbar GitHub](https://github.com/galkan/crowbar)

---

## 🖥️ 6. **Windows Server 2022**
- **Category**: Operating System (Active Directory Domain Controller)
- **What I did**: I set up **Windows Server 2022** as the **Active Directory Domain Controller** (ADDC) for the `geo.global` domain. I configured it to manage users and groups, like **John Doe** and **Susan Smith**, for the IT and HR organizational units.
- **How I used it**: I created a centralized authentication system for my lab and configured it to forward logs to **Splunk** for monitoring. For example, when I simulated an unauthorized account creation, the event was logged and visible in **Splunk** for blue team detection.
- **Purpose**: This system allowed me to replicate real-world Active Directory environments to simulate attacks and monitor responses.
- **Website**: [Windows Server Official Page](https://www.microsoft.com/en-us/windows-server)

---

## 💾 7. **Windows 10**
- **Category**: Operating System (Client Machine)
- **What I did**: I used **Windows 10** as the client machine for both red and blue team activities in the lab. It was configured to forward system logs to **Splunk**.
- **How I used it**: I attacked this machine using Kali Linux and **Atomic Red Team**, and I monitored its logs with Splunk. I also used **Sysmon** on this machine to capture detailed events like process creation and file access.
- **Purpose**: The Windows 10 machine played a central role in the attack and defense cycle, allowing me to simulate both offensive and defensive security operations.
- **Website**: [Windows 10 Official Page](https://www.microsoft.com/en-us/software-download/windows10)

---

## 🔧 8. **Splunk Universal Forwarder**
- **Category**: Log Forwarder
- **What I did**: I installed the **Splunk Universal Forwarder** on both the **Windows Server 2022 (Active Directory)** and **Windows 10** client. This allowed me to forward system and security logs to my central **Splunk Server**.
- **How I used it**: The forwarder ensured that real-time logs from both machines were sent to **Splunk** for analysis. I configured it to capture important events like user logins, process creation, and network connections.
- **Purpose**: This allowed me to continuously monitor the lab’s activity and detect potential security incidents in real-time.
- **Website**: [Splunk Universal Forwarder Download](https://www.splunk.com/en_us/download/universal-forwarder.html)
