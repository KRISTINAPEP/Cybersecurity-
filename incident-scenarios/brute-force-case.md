# Mock Incident Report – Brute Force Case

## Summary
Multiple failed login attempts were detected on server `web01`. Investigation confirmed brute force activity targeting the `admin` account.

## Indicators
- 300+ failed login attempts from IP `192.168.1.45`
- Attempts occurred within a 10-minute window
- Targeted username: `admin`

## Investigation Steps
- Used `grep "Failed password" /var/log/auth.log` to find failed login entries
- Used `awk` and `uniq -c` to count attempts per user
- Verified source IP and time stamps

## Response Actions
- Blocked IP via firewall
- Reset password for `admin`
- Enabled MFA for privileged accounts
- Logged incident in ticketing system

## Lessons Learned
- Implement rate limiting for login attempts
- Monitor auth logs daily
- Conduct security awareness training for admins
