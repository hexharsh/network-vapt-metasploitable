# NET-05: Insecure FTP Configuration

| Field | Value |
|---|---|
| Severity | **Medium** |
| CVSS v3.1 base score | 5.3 `[CONFIRM]` |
| Affected service | 21/tcp FTP |
| CVE / Reference | N/A |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

FTP allows cleartext authentication and/or anonymous access.

## Steps to Reproduce (lab only)

1. Run `nmap --script ftp-anon -p 21 <TARGET_IP>`.
2. Attempt anonymous login `[ADD result]`.

## Evidence

- Screenshot: `[ADD evidence/NET-05-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Data exposure and credential sniffing.

## Remediation

- Disable anonymous login.
- Replace FTP with SFTP or FTPS.
