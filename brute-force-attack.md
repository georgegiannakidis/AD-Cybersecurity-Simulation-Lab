# Brute Force Attack Using Crowbar

In this guide, I’ll explain how I carried out a brute force attack on the Windows 10 client using **Crowbar** from my **Kali Linux** machine.

## 🔨 Step 1: Set Up Crowbar on Kali Linux

### 1.1 Installing Crowbar
First, I installed **Crowbar** on my **Kali Linux** machine using the following command:
```bash
sudo apt install crowbar
```
### 1.2 Selecting the Target
I targeted the Windows 10 machine (192.168.10.10) and specified the RDP protocol for the attack.

## ⚔️ Step 2: Running the Brute Force Attack
### 2.1 Command Used
I executed the following command to start the brute force attack:

```bash
crowbar -b rdp -s 192.168.10.10 -u susan.smith -C /path/to/password_list.txt
```
### 2.2 Successful Login
After trying several passwords, I successfully cracked the password for Susan Smith (wH0ish1r!nG) and gained access to the Windows 10 machine via RDP.

## 🎯 Conclusion
This attack showed how brute force techniques can be used to gain unauthorized access. I used Splunk to monitor and log all failed and successful attempts, which provided valuable insight for blue team activities.
