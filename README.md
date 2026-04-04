# 🔐 Advanced Splunk SIEM Threat Detection

📌 Introduction

This project demonstrates how a Security Operations Center (SOC) analyst uses Splunk SIEM to detect suspicious activities from system logs. The main focus of this project is identifying authentication-based attacks such as failed login attempts and Kerberos-based attacks.

Splunk is a powerful SIEM (Security Information and Event Management) tool used to collect, search, and analyze logs in real-time for threat detection.

---

🎯 Objective

- To analyze system and security logs using Splunk
- To detect suspicious login attempts
- To identify Kerberos authentication attacks
- To understand real-world SOC monitoring techniques

---

🛠 Tools Used

- Splunk Enterprise (Free version)
- Log datasets (Windows/Linux logs)
- Laptop for log ingestion and analysis

---

📊 Architecture Diagram

Logs (Windows/Linux Systems)
            ↓
     Splunk SIEM Platform
            ↓
     Search Queries (SPL)
            ↓
     Threat Detection
            ↓
     Alert / Investigation

---

📂 Data Source

- Windows Security Logs
- Authentication logs (Kerberos, login attempts)

---

🔍 Detection Use Cases

1. Failed Login Detection

Detect multiple failed login attempts which may indicate brute force attacks.

🔎 SPL Query:

index=windows EventCode=4625
| stats count by Account_Name, host
| sort - count

---

2. Successful vs Failed Logins

Compare login behavior.

🔎 SPL Query:

source="WinEventLog:Security"
(EventCode=4624 OR EventCode=4625)
| eval status=if(EventCode=4624,"Success","Failure")
| stats count by status

👉 This helps identify abnormal login patterns

---

3. Kerberos Authentication Failure Detection

Detect Kerberos-based failed authentication attempts.

🔎 SPL Query:

index=windows EventCode=4771 Status=0x18
| stats count by IpAddress, TargetUserName
| sort - count

👉 EventCode 4771 with status 0x18 indicates wrong password attempts

---

4. Brute Force Attack Detection (Advanced)

Detect repeated login failures from same IP.

🔎 SPL Query:

index=windows EventCode=4625
| stats count by src_ip
| where count > 5
| sort - count

👉 Multiple failed attempts indicate brute force behavior

---

5. Suspicious User Activity Detection

Detect unusual login behavior.

🔎 SPL Query:

index=windows EventCode=4624
| stats count by Account_Name
| sort - count

---

📈 Findings

- Identified multiple failed login attempts
- Detected repeated login failures from same IP
- Observed Kerberos authentication failures
- Indicated possible brute force and password spraying attacks

---

🧠 Real-World Scenario

In an enterprise environment, attackers often attempt to guess passwords by sending multiple login requests. These activities generate logs, which are collected and analyzed by SIEM tools like Splunk.

For example, repeated Kerberos authentication failures from a single IP may indicate a password spraying attack, which can lead to unauthorized access if not detected early

---

✅ Advantages

- Real-time threat detection
- Centralized log monitoring
- Helps SOC analysts respond quickly
- Supports investigation and forensics

---

❌ Limitations

- Requires proper configuration
- Generates large amount of data
- Needs skilled analysts to interpret results

---

📌 Conclusion

This project demonstrates how Splunk SIEM can be used to detect and analyze security threats from logs. By using SPL queries, we can identify suspicious activities such as failed logins and Kerberos attacks.

This project builds a strong foundation for SOC Analyst roles and real-world cybersecurity monitoring.

---

🚀 Future Improvements

- Create dashboards for visualization
- Configure real-time alerts
- Integrate with threat intelligence tools
- Automate incident response

---

💼 Placement Ready Statement

"I worked on a Splunk SIEM project where I analyzed authentication logs and detected suspicious activities such as failed login attempts, brute force attacks, and Kerberos-based authentication failures using SPL queries."
