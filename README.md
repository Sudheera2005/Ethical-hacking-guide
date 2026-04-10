Ethical Hacking & Malware Analysis: WannaCry Case Study
This repository contains the documentation and technical workflow for my college module assignment on Ethical Hacking. The project focuses on a controlled analysis of the WannaCry ransomware, simulating a full attack lifecycle from initial reconnaissance to maintaining persistence within a sandbox environment.

⚠️ Disclaimer
This project is for educational and research purposes only. All activities were performed in a strictly isolated, host-only virtual laboratory environment. Unauthorized access to computer systems is illegal.

🛠 Project Overview
The objective of this assignment was to understand the mechanics of self-propagating malware and the vulnerabilities it exploits (specifically MS17-010 / EternalBlue).

Environment Setup
Hypervisor: VirtualBox

Attacker Machine: Kali Linux

Victim Machine: Windows 7 (Unpatched / Vulnerable)

Network: Isolated Host-Only Adapter

🚀 Attack Lifecycle
1. Information Gathering & Reconnaissance
The first phase involved identifying the target on the local network and discovering open ports.

Tool: Nmap

Key Finding: Detected port 445 (SMB) open, indicating a potential vector for SMB-based exploits.

2. Vulnerability Scanning
To confirm if the target was susceptible to the EternalBlue exploit used by WannaCry.

Tool: Nmap Scripting Engine (NSE)

Command: nmap -p 445 --script smb-vuln-ms17-010  192.168.56.102

3. Exploitation (The Attack)
Utilized the Metasploit Framework to gain unauthorized access to the victim machine.

Exploit: exploit/windows/smb/ms17_010_eternalblue

Payload: windows/x64/meterpreter/reverse_tcp

Outcome: Successfully gained a Meterpreter shell with SYSTEM-level privileges.

4. Post-Exploitation & Persistence
To simulate how malware stays active after a reboot, I implemented basic persistence mechanisms.

Technique: Registry Run Key modification.

Tool: Meterpreter persistence module / reg commands.

5. Malware Analysis (WannaCry)
Behavioral Analysis: Observed the encryption process, the "Wana Decrypt0r" UI popup, and the file extension changes (.wnry).

Traffic Analysis: Used Wireshark to monitor the "Kill-switch" domain request (iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com).

📂 Repository Structure
/docs: Detailed assignment report (PDF).

/screenshots: Visual evidence of the Nmap scans and successful shell.

/scripts: Basic automation scripts used during the lab.

🎓 Learning Outcomes
Deep understanding of the SMB protocol and its vulnerabilities.

Proficiency in the Metasploit Framework and Nmap.

Insight into the importance of patch management and the "Kill-switch" mechanism in global cyber incidents.
