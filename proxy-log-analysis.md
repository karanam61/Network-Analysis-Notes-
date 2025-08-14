# Proxy Log Analysis

Proxies control access to HTTP, HTTPS, FTP, etc., based on policy.  
They query a category DB for the requested domain and apply **block** or **pass** actions.

## Example Analysis
- **act**: blocked
- **app**: https
- **src**: Internal server IP
- **dst**: Target IP
- **policy**: Block_Risk_Category_Policy
- **category**: 194 → Suspicious Content

## Analyst Actions
- Identify process/user making request.
- Cross-check with EDR/XDR logs for process origin.
- Determine if compromised system is attempting covert comms.

**Risks detected via proxy logs:**
- Malware beaconing to C2
- Policy evasion attempts
- Access to risky/malicious content categories
