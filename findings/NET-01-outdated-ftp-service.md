# NET-01: Outdated FTP Service with Known Critical Vulnerability

| Field | Value |
|---|---|
| Severity | **Critical** |
| CVSS v3.1 base score | 9.8 `[CONFIRM]` |
| Affected service | 21/tcp FTP `[ADD version]` |
| CVE / Reference | `[ADD CVE]` |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

The FTP service runs a version with a publicly known vulnerability that can lead to remote command execution.

## Steps to Reproduce (lab only)

1. Identify version with `nmap -sV -p 21 <TARGET_IP>`.
2. Correlate the version with Nessus results / public advisories `[ADD CVE]`.
3. Exploit in the lab with `[ADD Metasploit module or manual technique]`.
4. Confirm access level with `id` `[ADD result]`.

## Evidence

- Screenshot: `[ADD evidence/NET-01-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Remote, unauthenticated attacker could execute commands on the host.

## Remediation

- Upgrade to a supported, patched FTP server or remove the service.
- Restrict access with a host firewall.
- Monitor for unexpected listening ports.
