# VPN Log Analysis

VPNs are essential for secure remote access, making their logs critical for SOC analysts.  
Since VPN services are publicly exposed, they represent a prime attack surface.

---

## Key Log Fields
- **date** – Date of the event
- **time** – Time of the event
- **devname** – Hostname of the device
- **devid** – Device ID
- **eventtime** – Event timestamp (epoch format)
- **tz** – Time zone offset
- **logid** – Log ID
- **type** – Log type (traffic, event, etc.)
- **subtype** – VPN, webfilter, virus, etc.
- **level** – Severity
- **logdesc** – Description
- **action** – System action taken
- **tunneltype** – SSL, IPSec, etc.
- **remip** – Remote IP initiating VPN
- **user** – Authenticated username
- **reason** – Access result
- **msg** – Status message

---

## Critical Analysis Points
- Source IP of connection
- Authenticated username
- Success/failure status

---

## Common Detections
- Successful/unsuccessful VPN logins
- Brute-force attempts
- Access from non-approved geos/times

---

**Example:**  
Successful VPN access → request IP `13.29.5.4`, username `letsdefend-user`, message `login successfully`.
