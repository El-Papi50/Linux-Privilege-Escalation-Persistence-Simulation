# Linux-Privilege-Escalation-Persistence-Simulation ( Incident Report)
This project simulates a Linux privilege escalation and persistence attack within a controlled Ubuntu lab environment. The objective was to intentionally misconfigure the system, simulate compromise, detect malicious activity using system logs, and perform structured incident response remediation.

This lab demonstrates practical Blue Team skills including log analysis, user account auditing, privilege investigation, and containment procedures.

🖥 Lab Environment

OS: Ubuntu 22.04 LTS
Platform: VirtualBox
Log Source: systemd journal (journalctl)
Monitoring Tools: Native Linux logging


🔎 Attack Simulation
Stage 1: Misconfiguration

- Created user account intern

- Granted excessive privileges (sudo group)

- Enabled passwordless sudo access

Stage 2: Privilege Escalation

- intern escalated privileges using sudo

- Root session opened

Stage 3: Persistence

- Created unauthorized administrative account: sysbackup

- Added account to sudo group

- Modified cron for persistence
- 

🧾 Evidence Collected

usermod: add 'sysbackup' to group 'sudo'
sudo: session opened for user root(uid=0) by intern(uid=1001)
Suspicious Artifacts

Unauthorized user account: sysbackup

- Modification of /etc/group

- Cron job modification

- Repeated root session openings

🕒 Timeline Reconstruction

Time	    Event
19:50:13	Intern initiated sudo session
20:02:21	Privilege escalation to root
20:04:26	Creation of sysbackup user
20:04:26	Added to sudo group
20:05:50	Cron modification detected


🛡 Incident Response Actions

- Removed unauthorized user accounts

- Revoked sudo privileges from intern

- Restored secure sudo configuration

- Removed malicious cron entries

- Reset credentials

- Reviewed user and group integrity


📊 Root Cause Analysis

The compromise was enabled by:

- Excessive privilege assignment

- Passwordless sudo configuration

- Lack of monitoring alerts

- Absence of least-privilege enforcement


🔐 Security Recommendations

- Enforce least-privilege model

- Disable passwordless sudo

- Enable audit rules for user management

- Deploy Host Intrusion Detection (Wazuh/OSSEC)

- Implement centralized logging (SIEM)


🎯 Skills you'll have demonstrated

- Linux log analysis

- Privilege escalation detection

 - User account auditing

- Timeline reconstruction

- Incident containment

- Security hardening

📈 Why This Project Matters

This lab mirrors real-world insider threat or post-exploitation scenarios. It demonstrates practical incident response capability beyond theoretical knowledge.
