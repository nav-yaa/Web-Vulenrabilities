# SSRF
Server-Side Request Forgery (SSRF) is a vulnerability that allows an attacker to make the server send unauthorized requests on its behalf — typically to internal systems or third-party services.

# Why is SSRF Dangerous?
SSRF is dangerous because it allows attackers to:
- Access internal services (e.g., metadata APIs like AWS 169.254.169.254)
- Bypass firewalls or network segmentation
- Scan internal ports or service
- Exfiltrate sensitive data


# Mitigation 
- Block access to internal IP ranges: 127.0.0.1
- Use metadata service protection
- Disable unused services that process URL


