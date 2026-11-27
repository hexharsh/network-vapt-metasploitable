# NET-03: Weak or Default Credentials on Network Services

| Field | Value |
|---|---|
| Severity | **High** |
| CVSS v3.1 base score | 8.8 `[CONFIRM]` |
| Affected service | `[ADD services, e.g., SSH, FTP, database]` |
| CVE / Reference | N/A |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

One or more services accepted weak or default username/password combinations.

## Steps to Reproduce (lab only)

1. Enumerate services that accept credentials.
2. Test a small, targeted wordlist against lab services only `[ADD tool used]`.
3. Record successful logins (do not publish passwords) `[ADD result]`.

## Evidence

- Screenshot: `[ADD evidence/NET-03-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Attackers could log in directly and pivot to further compromise.

## Remediation

- Change all default passwords.
- Enforce password complexity and account lockout.
- Prefer key-based authentication for SSH.
