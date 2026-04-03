# Advanced Splunk SIEM Threat Detection Project
---
## Objective
To perform advanced log analysis using Splunk SIEM and detect real-world cyber threats such as brute force attacks, unauthorized root access, and abnormal login behavior.
---
## Tools Used
- Splunk Enterprise
- Loghub Dataset (Linux Logs)
---
## Dataset
Linux 2k log file from Loghub dataset containing authentication and system activity logs.
---
## Project Overview
This project simulates a real-world Security Operations Center (SOC) environment where logs are continuously monitored to detect malicious activities. Splunk is used as a SIEM tool to collect, search, analyze, and visualize log data.
---
## Steps Performed
1. Installed Splunk Enterprise
2. Uploaded and indexed Linux log dataset
3. Explored log events using basic search queries
4. Applied advanced SPL queries for threat detection
5. Identified suspicious login patterns
6. Detected brute force attack attempts
7. Monitored root user activities
8. Created interactive dashboards for visualization
---
## Advanced Search Queries

### 1. Detect Brute Force Attack
index=* "failed" OR "failure" | stats count by src | sort -count
---
### 2. Detect Multiple Failed Logins Over Time
index=* "failed" | timechart count
---
### 3. Detect Root User Activity
index=* user=root | stats count by src
---
### 4. Identify Top Source IPs
index=* | top src
---
### 5. Successful vs Failed Logins
index=* ("failed" OR "success") | stats count by action
---
## Findings
- Multiple failed login attempts detected from specific IP addresses
- High frequency of login failures indicates possible brute force attack
- Root user login attempts observed, indicating high-risk activity
- Certain IP addresses showed repeated suspicious behavior
---
## Dashboard Panels
- Failed Login Attempts Over Time
- Top Source IPs
- Root User Activity
- Login Success vs Failure Comparison
---
## Conclusion
This project demonstrates how Splunk SIEM can be used to detect cyber threats in real-time. By analyzing log data and creating dashboards, security analysts can quickly identify suspicious patterns and respond to potential attacks.
---
## Skills Gained
- SIEM Fundamentals
- Log Analysis
- SPL Query Writing
- Threat Detection
- Security Monitoring
- Dashboard Creation
---
