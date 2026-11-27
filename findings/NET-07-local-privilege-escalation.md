# NET-07: Local Privilege Escalation Path

| Field | Value |
|---|---|
| Severity | **High** |
| CVSS v3.1 base score | 7.8 `[CONFIRM]` |
| Affected service | `[ADD vector, e.g., SUID binary, kernel, misconfigured service]` |
| CVE / Reference | `[ADD CVE if applicable]` |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

A low-privileged account could escalate to root through `[ADD vector]`.

## Steps to Reproduce (lab only)

1. From a low-privileged lab shell, enumerate the host (kernel version, SUID binaries, sudo rights, cron jobs).
2. Validate the escalation vector `[ADD steps]`.
3. Confirm with `id` showing uid=0 `[ADD evidence]`.

## Evidence

- Screenshot: `[ADD evidence/NET-07-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Any initial foothold becomes full root compromise.

## Remediation

- Patch kernel and vulnerable packages.
- Remove unnecessary SUID bits and tighten sudo rules.
- Apply least privilege to services.
