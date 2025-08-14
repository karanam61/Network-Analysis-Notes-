# NetFlow Log Analysis

NetFlow provides high-level network flow summaries, not individual packet details.

Think of it like a CCTV camera: it records:
- Who talked to whom
- When
- How much data was transferred  
Strictly based on IPs.

**Key Points:**
- Records conversations (flows) between IP addresses.
- Includes timestamps, duration, byte/packet counts.
- Useful for identifying top talkers, suspicious data exfiltration, and unusual communication patterns.

