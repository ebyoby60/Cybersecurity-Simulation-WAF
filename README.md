📌 Project Overview
This project demonstrates a full-scale security lifecycle within a virtualized enterprise environment. Using Kali Linux as the attacker and Ubuntu as the victim, I deployed a vulnerable web application, simulated real-world cyber attacks, implemented a Web Application Firewall (WAF), and analyzed security logs to verify mitigation.

🛠️ Tech Stack & Tools
Virtualization: VMware Workstation

Attacker OS: Kali Linux 2025.2

Victim OS: Ubuntu 24.04 (Server)

Web App: DVWA (Damn Vulnerable Web App)

Security: ModSecurity WAF with OWASP Core Rule Set (CRS)

Monitoring: Apache2 Error Logs & Netcat Listener

🏗️ Network Architecture
The simulation consists of a controlled subnet where the Attacker and Victim communicate via a NAT/Host-Only network.

Attacker (Kali): 192.168.147.129

Victim (Ubuntu): 192.168.147.131

🚀 Simulation Phases
1. Deployment (The Environment)
I configured an Ubuntu server running a LAMP stack to host DVWA. Additionally, I deployed a Netcat-based Honeypot on port 8080 to capture unauthorized connection attempts.

2. The Attack (Offensive)
Using Kali Linux, I performed the following:

Reconnaissance: Conducted nmap scans to identify open ports and services.

Exploitation: Simulated Cross-Site Scripting (XSS) and SQL Injection (SQLi) attacks on the web application.

Honeypot Interaction: Established a connection to the hidden listener to test detection capabilities.

3. The Defense (Defensive)
To mitigate the attacks, I configured ModSecurity:

Installed libapache2-mod-security2.

Activated the SecRuleEngine by transitioning from DetectionOnly to On.

Applied the OWASP Core Rule Set to filter malicious HTTP traffic.

4. Monitoring & Results
Post-mitigation, all attack attempts resulted in an HTTP 403 Forbidden error. I verified the security logs in /var/log/apache2/error.log, which confirmed that the WAF successfully identified the attacker's IP and blocked the payloads.

📊 Key Deliverables
Security Logs: Detailed logs showing "Access Denied" for blocked IPs.

Evidence: Screenshots of successful attack detection and 403 Forbidden responses.

Incident Report: A formal summary of findings and mitigation steps.

💡 Lessons Learned
Importance of Defense in Depth: A WAF is a critical layer for protecting vulnerable legacy code.

Log Analysis: Understanding how to read WAF anomaly scores is essential for identifying sophisticated threats.

Proactive Monitoring: Using honeypots provides early warning signs of lateral movement or scanning.
