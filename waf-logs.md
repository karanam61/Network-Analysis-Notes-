# WAF Log Analysis

WAFs protect web servers, often with SSL offloading for HTTPS inspection.

## Key Log Fields
- date/time
- type, main_type, sub_type
- severity_level
- proto, service
- action, policy
- src/dst IP & ports
- http_method, http_url, http_host
- msg, signature_subclass
- attack_type

## Process
- Check src/dst
- Validate WAF action (block/alert)
- Review HTTP status codes
- Determine if attack reached server

## Common Detections
- SQLi
- XSS
- Code injection
- Suspicious HTTP methods (PUT, DELETE)
