# Incident Simulation: Blocked Malicious Website

**Role:** SOC Analyst (Simulated Environment)  
**Environment:** TryHackMe  
**Date:** 02/03/2026  

**Scope:** This investigation was conducted in TryHackMe Phishing Simulation, Splunk Enterprise lab environment.

## Summary
User attempted to access a blacklisted external URL. Firewall successfully blocked the outbound request before connection occurred, preventing potential malware infection or credential compromise.

## Alert Overview
- **Alert Name:** Access to Blacklisted External URL Blocked by Firewall
- **Detection Source:** Firewall/Proxy
- **Severity:** High
- **Trigger Condition:** Outbound request to URL listed in organization blacklist/threat intelligence feeds

## Affected Entities
- **User:** Hannah Harris-HR
- **Source IP/Device:** 10.20.2.17

## Investigation Steps
1. Took ownership of alert in Splunk queue; Reviewed associated playbooks for general direction.
2. Reviewed firewall logs for source IP 10.20.2.17 at timestamp 02/03/2026 22:24:54
3. Verified destination IP 67.199.248.11 against threat intelligence using TryDetectThis and VirusTotal; confirmed as malicious.
4. Confirmed firewall rule "Blocked Websites" successfully prevented connection on Port 80 (HTTP/unencrypted)

## Key Findings
- **IOCs:** 
  - Source IP: 10.20.2.17
  - Destination IP: 67.199.248.11
  - URL: http://bit.ly/3sHkX3da1234
  - Protocol: TCP Port 80 (unencrypted)
  
- **Patterns Observed:** User accessed blocked URL via web-browsing application; firewall rule triggered and blocked connection before data exchange

## Conclusion
**Verdict:** True Positive/Malicious  
**Attack Type:** Phishing/Malicious Website Access  
**Reasoning:** Destination IP and URL confirmed malicious by threat intelligence. Firewall successfully prevented compromise. Even if accidental, user needs awareness training to avoid future attempts.

## Recommended Actions
- User awareness training on identifying phishing/malicious URLs and safe browsing practices
- Monitor user account and source IP for additional suspicious activity

## Tools Used
- Splunk Enterprise
- VirusTotal
- TryDetectThis (Specialized, internal IP/URL threat checker tool on THM)

## MITRE ATT&CK
T1204.001 – User Execution: Malicious Link

## Lessons Learned
Ive learned that Firewall blocks are effective prevention, but user education is important. Knowing *why* users click malicious links helps improve awareness training and reduce future incidents.