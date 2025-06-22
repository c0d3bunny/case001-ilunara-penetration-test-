# Penetration Test Report: ilunara.com
**Date:** 2025-06-22  
**Author:** c0d3bunny (Tina)  
**Type:** External Reconnaissance & Web Vulnerability Assessment  
**Scope:** Public-facing web assets of `ilunara.com`  
**Tools Used:** Nmap, Nikto, Gobuster, WhatWeb, dig, whois

---

## 1. Reconnaissance Summary

- Domain is protected via Cloudflare, DNS obfuscated
- WHOIS data hidden by WithheldForPrivacy (Reykjavik)
- DNSSEC not implemented
- Only active subdomain discovered: `www.ilunara.com`

---

## 2. Open Ports

| Port | Protocol | Status | Notes |
|------|----------|--------|-------|
| 80   | HTTP     | Open   | Cloudflare proxy |
| 443  | HTTPS    | Open   | Encrypted endpoint |
| 8080 | HTTP     | Open   | Alt web interface? |
| 8443 | HTTPS    | Open   | Possibly admin or staging proxy |

---

## 3. Web Server Information

- Web server: Cloudflare HTTP proxy
- HTML5 + standard headers detected
- Missing HTTP security headers:
  - `X-Frame-Options`
  - `X-Content-Type-Options`
- `/cdn-cgi/trace` endpoint exposed

---

## 4. Recommendations

- Implement missing HTTP headers
- Monitor port exposure (especially 8080/8443) if origin server ever leaks
- Consider removing `cdn-cgi/trace` endpoint or rate-limit it
- Review DNSSEC implementation for future integrity hardening

---

## 5. Screenshots & Logs

> See `/screenshots/` folder & attached raw output logs in `recon.txt`.

---

## 6. Disclaimer

This assessment was conducted as part of an authorized security exercise with permission from the domain owner. No data was modified, exfiltrated, or exploited during this operation.
