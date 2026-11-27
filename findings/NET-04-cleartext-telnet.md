# NET-04: Cleartext Telnet Remote Administration

| Field | Value |
|---|---|
| Severity | **High** |
| CVSS v3.1 base score | 7.4 `[CONFIRM]` |
| Affected service | 23/tcp Telnet |
| CVE / Reference | N/A |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

Telnet transmits credentials and session data in cleartext.

## Steps to Reproduce (lab only)

1. Confirm Telnet is open (`nmap -sV -p 23 <TARGET_IP>`).
2. Capture a lab login with Wireshark/tcpdump and observe cleartext credentials `[ADD result, values redacted]`.

## Evidence

- Screenshot: `[ADD evidence/NET-04-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Anyone on the network path can capture administrator credentials.

## Remediation

- Disable Telnet.
- Use SSH with key-based authentication.
