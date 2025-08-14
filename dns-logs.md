## Purpose
DNS translates domains to IPs; logs are useful for detecting suspicious lookups.

## Key Questions
- Access to non-approved/risky domains?
- Attempts to use DOT/DOH?
- Matches to Threat Intel IOCs?

## Log Sources
- DNS server events (audit logs)
- DNS query logs (must be enabled)

## Suspicious Patterns
- Random subdomains in short time → tunneling
- Servers making cloud service queries unexpectedly
- NXDOMAIN spikes
