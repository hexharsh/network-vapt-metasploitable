# NET-08: Web Server Misconfiguration

| Field | Value |
|---|---|
| Severity | **Medium** |
| CVSS v3.1 base score | 5.3 `[CONFIRM]` |
| Affected service | 80/tcp HTTP |
| CVE / Reference | N/A |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

Nikto identified default files, outdated web components, or information disclosure on the web server.

## Steps to Reproduce (lab only)

1. Run `nikto -h http://<TARGET_IP>`.
2. Manually verify each reported item `[ADD verified items]`.

## Evidence

- Screenshot: `[ADD evidence/NET-08-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Information disclosure that assists further attacks.

## Remediation

- Remove default and test applications.
- Disable directory listing and server version banners.
- Update web server and applications.
