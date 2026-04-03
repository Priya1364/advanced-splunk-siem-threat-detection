# Advanced Splunk SIEM Threat Detection Project
----
## Objective
To perform advanced log analysis using Splunk SIEM and detect real-world cyber threats such as brute force attacks, unauthorized root access, and abnormal login behavior.
----
## Tools Used
- Splunk Enterprise
- Loghub Dataset (Linux Logs)
----
## Dataset
Linux 2k log file from Loghub dataset containing authentication and system activity logs.
----
## Project Overview
This project simulates a real-world Security Operations Center (SOC) environment where logs are continuously monitored to detect malicious activities. Splunk is used as a SIEM tool to collect, search, analyze, and visualize log data.
----
## Steps Performed
1. Installed Splunk Enterprise
2. Uploaded and indexed Linux log dataset
3. Explored log events using basic search queries
4. Applied advanced SPL queries for threat detection
5. Identified suspicious login patterns
6. Detected brute force attack attempts
7. Monitored root user activities
8. Created interactive dashboards for visualization
----
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
----
index=* "failed"
| stats count by src
| where count > 10
----
## Findings
- Multiple failed login attempts detected from specific IP addresses
- High frequency of login failures indicates possible brute force attack
- Root user login attempts observed, indicating high-risk activity
- Certain IP addresses showed repeated suspicious behavior
----
## Dashboard Panels
- Failed Login Attempts Over Time
- Top Source IPs
- Root User Activity
- Login Success vs Failure Comparison
----
## Attack Scenario

The system logs show multiple failed login attempts from the same source IP address within a short period of time. This pattern indicates a possible brute force attack where an attacker is trying different passwords to gain unauthorized access.

Additionally, root user login activity was observed, which is considered a high-risk action. Unauthorized root access can lead to full system compromise.

This scenario simulates a real-world SOC investigation where analysts detect and respond to suspicious authentication behavior.

The SOC analyst monitors logs using Splunk to detect these malicious activities and prevent system compromise.
----
## Analyst Insight

The repeated failed login attempts suggest automated attack behavior. By analyzing the frequency and source of these attempts, it is possible to identify malicious actors.

Monitoring root user activity is critical because attackers often try to gain elevated privileges after initial access.

Using Splunk dashboards, security analysts can quickly visualize these patterns and take immediate action.
----
## SOC Analysis Workflow
1. Logs are ingested into Splunk
2. Analyst searches for suspicious login patterns
3. Detection queries identify abnormal behavior
4. Analyst investigates repeated failed attempts
5. Suspicious IPs are identified
6. Alerts and dashboards are used for monitoring
----
## Threat Classification
- Brute Force Attack (Multiple failed logins)
- Privilege Escalation (Root access attempts)
- Suspicious Login Behavior (Unusual patterns)
----
## Real-World Impact
If these attacks are not detected:
- Unauthorized access may occur
- Sensitive data may be stolen
- System may be compromised
Early detection using SIEM helps prevent major security incidents.
----
## Conclusion
This project demonstrates how Splunk SIEM can be used to detect cyber threats in real-time. By analyzing log data and creating dashboards, security analysts can quickly identify suspicious patterns and respond to potential attacks.
----
## Skills Gained
- SIEM Fundamentals
- Log Analysis
- SPL Query Writing
- Threat Detection
- Security Monitoring
- Dashboard Creation
----
## Dashboard Explanation

The dashboard provides a visual representation of security events:

- Failed Login Attempts: Shows frequency of login failures over time
- Top Source IPs: Identifies the most active IP addresses involved in suspicious activity
- Root Activity: Displays attempts involving privileged user access
- Success vs Failure: Compares authentication outcomes

These visualizations help analysts detect anomalies quickly.
---+
FINAL DASHBOARD STRUCTURE
1. Failed Login Trend (timechart)
2. Top Attacker IPs
3. Root User Activity
4. Success vs Failure
5. High Risk IPs (count > 10)
----
