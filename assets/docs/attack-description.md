# Attack Description: Red Team vs Blue Team

This document provides an overview of the attack simulations I ran in the **AD-Cybersecurity-Simulation-Lab** and how I monitored them.

## ⚔️ Red Team Activity: Brute Force Attack

### 1.1 Attack Setup
I used **Kali Linux** to simulate a brute force attack against the Windows 10 client. Using the **Crowbar** tool, I attempted to crack the credentials of **Susan Smith** from the HR organizational unit.

### 1.2 Running the Brute Force Attack
To perform the attack, I ran **Crowbar** with a password list and targeted the Windows Remote Desktop service. After a few failed attempts, I was able to crack the password `wH0ish1r!nG` and gain access to the machine.

## 🛡️ Blue Team Response: Log Monitoring with Splunk

### 2.1 Monitoring Logs in Splunk
Once the attack was underway, I used **Splunk** to monitor login attempts from the Windows 10 machine. By filtering the logs with **Event ID 4625** (failed logins) and **Event ID 4624** (successful logins), I was able to detect the brute force attempt and successful login.

### 2.2 Setting Alerts
I also configured **Splunk alerts** to notify me when there were a series of failed login attempts followed by a successful one, which is a strong indicator of a brute force attack.

## 🎯 Conclusion
This simulation demonstrated how a brute force attack can be detected and mitigated using **Splunk** as a central log analysis tool.
