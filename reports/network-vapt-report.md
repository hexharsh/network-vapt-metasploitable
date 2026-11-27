# Network Vulnerability Assessment and Penetration Test Report

Prepared by Harsh ([@hexharsh](https://github.com/hexharsh)) · Version 1.0 (public, sanitized) <!-- TODO: test dates -->

Target: Metasploitable 2 lab VM (`<TARGET_IP>`) on an isolated host-only network that I own. Exploitation was limited to this VM.

---

## 1. Executive Summary

A network penetration test of the Metasploitable 2 lab host identified **8 findings**: 2 Critical, 4 High, and 2 Medium. The host runs multiple outdated, unsupported services with publicly known exploits, accepts weak credentials, and exposes cleartext management protocols. <!-- TODO: add one sentence on what access you reached, e.g. "root-level access was obtained through N independent paths." -->

The main root cause is the absence of patch management and service hardening. Upgrading the operating system, removing legacy services, and enforcing strong authentication would remove most of the risk.

| Severity | Count |
|---|---|
| Critical | 2 |
| High | 4 |
| Medium | 2 |

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

The full TCP scan showed a large number of exposed services, including FTP, SSH, Telnet, HTTP and SMB. Sanitized Nmap output, with the exact versions, is in [`../nmap/`](../nmap/).

<!-- TODO: optionally paste a port | service | version table from your scan -->

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



## 6. Exploitation Narrative

<!-- TODO: write 3-5 sentences in your own words: which finding gave you initial access, what level of access it gave, how you confirmed it, and what you did next. Keep IPs as placeholders. -->

## 7. Post-Exploitation

After gaining a shell I reviewed the current user and privileges, kernel and OS version, SUID binaries and sudo rights, readable sensitive files, and possible privilege escalation paths (see NET-07).

<!-- TODO: add your observations for each of these -->

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

Nmap, Nessus Essentials, Metasploit Framework, Netcat, Nikto. <!-- TODO: versions -->
