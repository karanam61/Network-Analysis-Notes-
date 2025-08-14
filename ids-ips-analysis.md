# IDS/IPS Log Analysis

IDS/IPS logs show intrusion attempts and prevention actions.  
Correlated with SIEM to link related events (e.g., port scan → exploit attempt).

## Key Checks
- Attack direction (inbound/outbound)
- Severity level (low → critical)
- Multiple signature triggers between same src/dst
- Service running on target port?
- Was attack blocked or just detected?

## Common Detections
- Port scans
- Vuln scans
- Code injection
- Brute force
- DoS/DDoS
- Trojan/botnet activity

