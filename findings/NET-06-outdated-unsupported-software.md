# NET-06: Outdated and Unsupported Operating System and Services

| Field | Value |
|---|---|
| Severity | **High** |
| CVSS v3.1 base score | 7.5 `[CONFIRM]` |
| Affected service | Host OS and multiple services |
| CVE / Reference | Multiple `[ADD from Nessus]` |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

The operating system and many services are end-of-life and no longer receive security updates.

## Steps to Reproduce (lab only)

1. Review Nessus results for end-of-life and missing-patch plugins `[ADD plugin IDs]`.
2. Confirm versions with banner grabbing (Netcat) and Nmap `-sV`.

## Evidence

- Screenshot: `[ADD evidence/NET-06-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Large number of exploitable known vulnerabilities.

## Remediation

- Migrate to a supported OS release.
- Implement regular patch management.
- Remove unused services.
