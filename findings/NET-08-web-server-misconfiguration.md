# NET-08: Web Server Misconfiguration

> **Medium** · CVSS 3.1 base 5.3 · 80/tcp HTTP · no CVE (configuration issue)

### What's wrong

Nikto identified default files, outdated web components, or information disclosure on the web server.

### Reproducing it in the lab

1. Run `nikto -h http://<TARGET_IP>`.
2. Manually verify each reported item <!-- TODO: verified items -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Information disclosure that assists further attacks.

### Recommended fix

- Remove default and test applications.
- Disable directory listing and server version banners.
- Update web server and applications.
