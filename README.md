RDP Brute Force Attack Analysis with Splunk

 Overview

Brute force attacks are a common technique used by attackers to gain unauthorized access by repeatedly attempting different username and password combinations.

In this project, I analyzed Windows Security Event Logs from a simulated RDP brute force attack using Splunk, with the goal of identifying attack patterns, targeted accounts, and potential indicators of compromise.

 Objectives
Detect brute force activity using log analysis
Identify targeted user accounts
Extract attacker source IP addresses
Confirm attack vector (RDP)
Analyze failure reasons and patterns
 Tools & Technologies
Splunk
Windows Security Event Logs
CSV Log Dataset
 Dataset
Source File: BTLO_Bruteforce_Challenge.csv
Contains Windows Event Logs including login attempts and authentication failures

 Key Log Indicators

The analysis focused on the following Windows Event IDs:

4625 → Failed logon attempt (primary indicator of brute force)
4624 → Successful logon (used to detect possible compromise)

 Investigation Steps
1. Identify Failed Login Attempts

Filtered logs for Event ID 4625 to detect suspicious authentication failures.

source="BTLO_Bruteforce_Challenge.csv" "4625"
2. Extract Important Fields

Used field extraction to capture key details:

Account Name
Source Network Address (IP)
Logon Type
Failure Reason


Logon Type 10 → Remote Interactive (RDP)
Confirms attack was conducted via RDP
