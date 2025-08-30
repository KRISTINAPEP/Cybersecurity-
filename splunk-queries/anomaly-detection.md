# Splunk Queries – Anomaly Detection

These SPL queries help detect suspicious login behavior and authentication anomalies. Each query includes a brief explanation to show how it supports threat detection.

---

## 1. Failed Login Attempts by User

**Query:**
index=auth sourcetype=linux_secure "Failed password" | stats count by user

**Explanation:**  
Searches for failed login attempts and counts how many times each user was targeted. Useful for spotting brute force attacks.

---

## 2. Top Source IPs for Failed Logins

**Query:**
index=auth sourcetype=linux_secure "Failed password" | stats count by src_ip | sort -count

**Explanation:**  
Shows which IP addresses are generating the most failed login attempts. Helps identify attackers or misconfigured systems.

---

## 3. Unusual Login Times

**Query:**
index=auth sourcetype=linux_secure "Accepted password" | eval hour=strftime(_time,"%H") | stats count by hour

**Explanation:**  
Counts successful logins by hour. Helps detect logins at odd hours (e.g., 2 AM) that might be suspicious.

---

## 4. Multiple Failed Logins Followed by Success

**Query:**
index=auth sourcetype=linux_secure ("Failed password" OR "Accepted password") | transaction user maxspan=5m | search eventcount>3 AND "Accepted password"

**Explanation:**  
Finds users who had several failed logins followed by a successful one within 5 minutes. Could indicate a brute force success.

---

## 5. Login Activity by Country (GeoIP)

**Query:**
index=auth sourcetype=linux_secure "Accepted password" | iplocation src_ip | stats count by Country

**Explanation:**  
Maps login IPs to countries. Helps detect logins from unexpected regions.

---

## 6. First-Time Login Detection

**Query:**
index=auth sourcetype=linux_secure "Accepted password" | dedup user | table _time, user, src_ip

**Explanation:**  
Shows the first login event per user. Useful for onboarding tracking or spotting new accounts.

---

## How These Queries Help in a SOC Environment

These queries support key SOC analyst tasks like:

- Detecting brute force attacks and login anomalies
- Identifying suspicious IPs and geolocations
- Monitoring user behavior and access patterns
- Supporting incident investigations and alert tuning

Documenting them here helps build a repeatable workflow and shows readiness for real-world detection and response.

