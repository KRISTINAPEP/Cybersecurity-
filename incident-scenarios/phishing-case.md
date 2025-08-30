# Mock Incident Report – Phishing Case

## Summary
An employee clicked a fake login link and entered credentials. Attacker used them to access internal systems.

## Indicators
- Suspicious email from `it-support@secure-login.com`
- Link redirected to `secure-login.co`
- Login logs show access from foreign IP

## Investigation Steps
- Reviewed email headers
- Checked login timestamps and IP geolocation
- Verified user activity post-compromise

## Response Actions
- Disabled account
- Reset credentials
- Reported domain
- Conducted phishing awareness training

## Lessons Learned
- Improve email filtering
- Train users to spot fake links
