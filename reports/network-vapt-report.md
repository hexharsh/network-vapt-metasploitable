# Network Vulnerability Assessment and Penetration Test Report

**Target:** Metasploitable 2 lab VM (`<TARGET_IP>`)
**Tester:** hexharsh
**Assessment period:** `[ADD dates]`
**Report version:** 1.0
**Classification:** Public portfolio (sanitized)

> This assessment was conducted entirely within an isolated, host-only virtual lab owned by the tester. Exploitation was limited to the Metasploitable 2 VM.

---

## 1. Executive Summary

A network penetration test of the Metasploitable 2 lab host identified **8 findings**: 2 Critical, 4 High, and 2 Medium. The host runs multiple outdated, unsupported services with publicly known exploits, accepts weak credentials, and exposes cleartext management protocols. During testing, `[ADD: e.g., root-level access was obtained through N independent paths]`.

The main root cause is the absence of patch management and service hardening. Upgrading the operating system, removing legacy services, and enforcing strong authentication would remove most of the risk.

| Severity | Count |
|---|---|
| Critical | 2 |
| High | 4 |
| Medium | 2 |
| Low | `[ADD]` |

## 2. Scope

| Item | Detail |
|---|---|
| In scope | Metasploitable 2 VM at `<TARGET_IP>` |
| Out of scope | Hypervisor, host machine, any other network |
| Network | Host-only, no internet connectivity |
| Test type | Black-box from the network, then post-exploitation review |

## 3. Methodology

1. **Reconnaissance:** host discovery and full TCP port scan (Nmap).
2. **Enumeration:** service/version detection, NSE scripts, banner grabbing (Nmap, Netcat), web scan (Nikto).
3. **Vulnerability assessment:** Nessus scan and manual CVE correlation.
4. **Exploitation:** controlled exploitation of validated vulnerabilities (Metasploit Framework, Netcat).
5. **Post-exploitation:** privilege review and local privilege escalation checks.
6. **Reporting:** CVSS v3.1 scoring and remediation planning.

## 4. Enumeration Results

| Port | Service | Version | Vulnerable? |
|---|---|---|---|
| `[ADD]` | `[ADD]` | `[ADD]` | `[ADD]` |

Raw outputs (sanitized): [`../nmap/`](../nmap/)

## 5. Findings

| ID | Finding | Severity | CVSS | Detail |
|---|---|---|---|---|
| NET-01 | Outdated FTP service with critical vulnerability | Critical | 9.8 | [link](../findings/NET-01-outdated-ftp-service.md) |
| NET-02 | SMB remote code execution | Critical | 9.8 | [link](../findings/NET-02-smb-remote-code-execution.md) |
| NET-03 | Weak/default credentials | High | 8.8 | [link](../findings/NET-03-weak-default-credentials.md) |
| NET-04 | Cleartext Telnet | High | 7.4 | [link](../findings/NET-04-cleartext-telnet.md) |
| NET-05 | Insecure FTP configuration | Medium | 5.3 | [link](../findings/NET-05-insecure-ftp-configuration.md) |
| NET-06 | Outdated/unsupported software | High | 7.5 | [link](../findings/NET-06-outdated-unsupported-software.md) |
| NET-07 | Local privilege escalation | High | 7.8 | [link](../findings/NET-07-local-privilege-escalation.md) |
| NET-08 | Web server misconfiguration | Medium | 5.3 | [link](../findings/NET-08-web-server-misconfiguration.md) |

> CVSS scores are typical base scores for these issue types and are marked `[CONFIRM]` in each finding until verified against evidence.

## 6. Exploitation Narrative

`[ADD a short, original narrative of your attack path: which finding gave initial access, what access level, and how you confirmed it. Keep IPs as placeholders.]`

## 7. Post-Exploitation

| Check | Observation |
|---|---|
| Current user / privileges | `[ADD]` |
| Kernel / OS version | `[ADD]` |
| SUID binaries / sudo rights | `[ADD]` |
| Sensitive files accessible | `[ADD type only]` |
| Privilege escalation | `[ADD]` |

## 8. Remediation Plan

| Priority | Action | Findings |
|---|---|---|
| Critical (immediate) | Patch or remove vulnerable FTP and Samba services | NET-01, NET-02 |
| High (7 days) | Remove default/weak credentials; disable Telnet | NET-03, NET-04 |
| High (30 days) | Upgrade OS and services; fix privilege escalation paths | NET-06, NET-07 |
| Medium (60 days) | Harden FTP and web server configuration | NET-05, NET-08 |

## 9. Conclusion

The target demonstrates how unpatched legacy services and weak authentication combine to allow full compromise. Defence should focus on patch management, attack-surface reduction, and strong authentication, followed by a retest.

## Appendix: Tools and Versions

Nmap `[ADD]`, Nessus Essentials `[ADD]`, Metasploit Framework `[ADD]`, Netcat, Nikto `[ADD]`.
