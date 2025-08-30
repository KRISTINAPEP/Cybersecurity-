# Splunk Alert – Brute Force Detection

## Scenario
Detect IP addresses with more than 100 failed login attempts in a short time window. This may indicate a brute force attack.

## SPL Query
index=auth sourcetype=linux_secure "Failed password" | stats count by src_ip | where count > 100

## Alert Configuration
- **Title:** Brute Force Detection Alert  
- **Trigger Condition:** Number of results > 0  
- **Schedule:** Every 5 minutes  
- **Actions:**  
  - Send email to SOC team  
  - Log to incident dashboard  
  - Optional: Run script to block IP

## Notes
This alert helps detect brute force attempts early and enables fast response. It can be tuned based on environment size and login frequency.
