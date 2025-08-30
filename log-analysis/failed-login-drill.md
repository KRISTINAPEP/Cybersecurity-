# Failed Login Investigation Drill

## Scenario
A system admin reports multiple failed login attempts on a Linux server. You’ve been asked to investigate.

## Commands Used

### `grep "Failed password" /var/log/auth.log`
Searches for failed login attempts in the authentication log.

### `grep "Failed password" /var/log/auth.log | wc -l`
Counts how many failed attempts occurred.

### `grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c`
Lists usernames involved and how many times each failed.

## Notes
This type of analysis helps detect brute force attempts and compromised accounts. It’s a core skill for SOC analysts monitoring authentication logs.
