---
title : "DNS Simulation"
date : 2026-07-07
weight : 4
chapter : false
pre : " <b> 5.4.4. </b> "
---

#### Validating Infrastructure Network Isolation
To conclusively demonstrate that the PawVerse database is completely obfuscated from the public internet domain, we simulate an external attacker performing a DNS Resolution Audit from outside the AWS perimeter.

1. Copy the active Amazon RDS MySQL Endpoint string (e.g., `pawverse-mysql.xxx.ap-southeast-1.rds.amazonaws.com`).
2. Open a localized Terminal (utilizing standard public internet routing, outside the target VPC) and execute:
   ```bash
   nslookup pawverse-mysql.xxx.ap-southeast-1.rds.amazonaws.com
   ```

![DNS Simulation nslookup](/images/5-Workshop/5.4-Database-Security/dns-nslookup.png)
*Figure 5.4.4.1: The DNS system denies IP resolution (No A/AAAA records) for queries originating from the public Internet.*

3. **Result Analysis:** Instead of returning an IP address like standard web domains, AWS Route 53 intercepts the query and returns a `No internal type for both IPv4 and IPv6 Addresses` error.
4. **Security Conclusion:** The network isolation defense parameter is functioning with 100% precision. AWS detects the external origin of the query and **refuses to resolve the DB's IP address**. Even if malicious actors acquire the exact Endpoint Name, they cannot obtain an IP to route their packets, entirely neutralizing remote brute-force attack vectors.