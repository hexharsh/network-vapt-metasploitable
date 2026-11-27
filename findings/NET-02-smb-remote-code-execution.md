# NET-02: SMB Service Vulnerable to Remote Code Execution

| Field | Value |
|---|---|
| Severity | **Critical** |
| CVSS v3.1 base score | 9.8 `[CONFIRM]` |
| Affected service | 139/445 tcp Samba `[ADD version]` |
| CVE / Reference | `[ADD CVE]` |
| Environment | Metasploitable 2, isolated host-only lab |

## Description

The Samba version in use is affected by a known vulnerability allowing remote code execution.

## Steps to Reproduce (lab only)

1. Enumerate SMB with Nmap NSE scripts (`smb-os-discovery`, `smb-enum-shares`).
2. Confirm version and vulnerability with Nessus `[ADD plugin ID]`.
3. Exploit in the lab with `[ADD module]`.
4. Record resulting access `[ADD result]`.

## Evidence

- Screenshot: `[ADD evidence/NET-02-*.png]`
- Command output (sanitized, IPs replaced):

```text
[ADD sanitized output]
```

## Impact

Full system compromise from the network.

## Remediation

- Patch Samba to a supported version.
- Disable SMBv1 and unnecessary shares.
- Restrict SMB to trusted internal hosts.
