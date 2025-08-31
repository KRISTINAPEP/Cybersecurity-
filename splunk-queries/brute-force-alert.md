# Splunk Alert – Brute Force Detection

## Scenario
Detect IP addresses with more than 100 failed login attempts in a short time window. This may indicate a brute force attack.

## SPL Query
`index=auth sourcetype=linux_secure "Failed password" | stats count by src_ip | where count > 100`

## Expected Output
| User     | Failed Logins |
|----------|----------------|
| admin    | 45             |
| jsmith   | 32             |
| guest    | 28             |

## Alert Configuration
- **Title:** Brute Force Detection Alert  
- **Trigger Condition:** Number of results > 0  
- **Schedule:** Every 5 minutes  
- **Actions:**  
  - Send email to SOC team  
  - Log to incident dashboard  
  - Optional: Run script to block IP

## SOC Relevance
Maps to MITRE ATT&CK T1110 (Brute Force). Helps detect credential stuffing or password spraying.

## Notes
This query simulates brute force detection logic in a Linux environment using Splunk SPL. It can be adapted for Windows logs or integrated into alert workflows.
