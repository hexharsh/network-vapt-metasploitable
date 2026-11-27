# Network VAPT — Metasploitable 2

> **Authorized lab only.** This assessment targeted Metasploitable 2, an intentionally vulnerable Linux VM published by Rapid7 for training. It ran on a **host-only virtual network that I own**, with no route to the internet or any other network. All exploitation was limited to this isolated lab VM.

![Type](https://img.shields.io/badge/Assessment-Network%20VAPT-blue) ![Scoring](https://img.shields.io/badge/Severity-CVSS%20v3.1-orange) ![Env](https://img.shields.io/badge/Environment-Host--only%20Lab-green)

## At a Glance

| Item | Detail |
|---|---|
| Target | Metasploitable 2 (Ubuntu 8.04 based VM) |
| Assessment type | Internal network vulnerability assessment and penetration test |
| Phases | Reconnaissance, enumeration, vulnerability assessment, exploitation, post-exploitation |
| Tools | Nmap, Nessus, Metasploit Framework, Netcat, Nikto |
| Full report | [reports/network-vapt-report.md](reports/network-vapt-report.md) |

## Lab Topology

```
┌──────────────────────────── Host-only virtual network (no internet) ────────────────────────────┐
│                                                                                                  │
│   ┌──────────────────────┐                                     ┌──────────────────────────┐       │
│   │  Attacker VM         │   Nmap / Nessus / Metasploit        │  Target VM               │       │
│   │  Kali Linux          │ ─────────────────────────────────▶ │  Metasploitable 2        │       │
│   │  <ATTACKER_IP>       │                                     │  <TARGET_IP>             │       │
│   └──────────────────────┘                                     └──────────────────────────┘       │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
Hypervisor: [ADD VirtualBox / VMware]   Network mode: Host-only   NAT/Bridged: disabled
```

> Real lab IP addresses are replaced with `<ATTACKER_IP>` and `<TARGET_IP>` throughout this repository.

## Methodology

Aligned with **PTES** (Penetration Testing Execution Standard) and **NIST SP 800-115**.

| Phase | Activities | Tools |
|---|---|---|
| 1. Reconnaissance | Host discovery, full TCP port scan | Nmap |
| 2. Enumeration | Service/version detection, NSE scripts, banner grabbing, web enumeration | Nmap, Netcat, Nikto |
| 3. Vulnerability assessment | Authenticated/unauthenticated scanning, CVE correlation | Nessus, Nmap NSE |
| 4. Exploitation | Controlled exploitation of validated findings | Metasploit Framework, Netcat |
| 5. Post-exploitation | Privilege level, local enumeration, privilege escalation paths | Shell commands, Metasploit modules |
| 6. Reporting | CVSS rating, impact, remediation | Markdown report |

## Enumeration Summary

Sanitized scan outputs are in [`nmap/`](nmap/).

| Port | Service | Version observed | Notes |
|---|---|---|---|
| 21/tcp | FTP | `[ADD from your scan]` | Cleartext protocol, anonymous login check |
| 22/tcp | SSH | `[ADD]` | Outdated version, weak credential check |
| 23/tcp | Telnet | `[ADD]` | Cleartext remote login |
| 80/tcp | HTTP | `[ADD]` | Nikto web scan |
| 139,445/tcp | SMB | `[ADD]` | Samba version and share enumeration |
| `[ADD]` | `[ADD]` | `[ADD]` | `[ADD other services you found]` |

## Findings

| ID | Finding | Severity | CVSS v3.1 | Impact | Remediation |
|---|---|---|---|---|---|
| NET-01 | Outdated FTP service with known critical vulnerability `[ADD version/CVE]` | Critical | 9.8 `[CONFIRM]` | Remote command execution | Upgrade or remove the service |
| NET-02 | SMB service vulnerable to remote code execution `[ADD version/CVE]` | Critical | 9.8 `[CONFIRM]` | Remote root compromise | Patch Samba, restrict SMB to trusted hosts |
| NET-03 | Weak / default credentials on network services | High | 8.8 `[CONFIRM]` | Unauthorized access | Enforce strong unique passwords, disable defaults |
| NET-04 | Cleartext Telnet remote administration | High | 7.4 `[CONFIRM]` | Credential interception | Disable Telnet, use SSH with keys |
| NET-05 | Insecure FTP configuration (cleartext / anonymous access) | Medium | 5.3 `[CONFIRM]` | Data exposure, credential sniffing | Disable anonymous access, use SFTP/FTPS |
| NET-06 | Outdated, unsupported services and OS | High | 7.5 `[CONFIRM]` | Many known CVEs exploitable | Upgrade to a supported OS and service versions |
| NET-07 | Local privilege escalation path `[ADD vector]` | High | 7.8 `[CONFIRM]` | Low-privileged user gains root | Patch kernel/software, remove misconfigured SUID binaries |
| NET-08 | Web server misconfigurations identified by Nikto `[ADD]` | Medium | 5.3 `[CONFIRM]` | Information disclosure | Remove default files, harden configuration |

Detailed write-ups: [findings/](findings/). Severity is rated with CVSS v3.1 base scores; `[CONFIRM]` markers mean the vector must be checked against my own evidence before publishing.

## Exploitation Summary

| Finding | Approach | Result | Evidence |
|---|---|---|---|
| NET-01 | `[ADD Metasploit module or manual method]` | `[ADD e.g., shell as root]` | `[ADD evidence file]` |
| NET-02 | `[ADD]` | `[ADD]` | `[ADD]` |
| NET-03 | Credential testing against lab services with a small wordlist | `[ADD]` | `[ADD]` |

All exploitation was performed **only against the Metasploitable 2 VM in my isolated host-only lab**. No exploit was run against any other host.

## Post-Exploitation Observations

- **Access level obtained:** `[ADD user / root]`
- **Local enumeration:** OS and kernel version, users and groups, SUID binaries, cron jobs, writable files `[ADD what you observed]`
- **Privilege escalation opportunities:** `[ADD vectors you validated]`
- **Sensitive data accessible:** `[ADD type of data, no real values]`
- **Persistence:** not established (out of scope for this lab)

## Remediation Priorities

1. **Patch or remove** outdated services (FTP, Samba, others listed in findings).
2. **Disable cleartext protocols** (Telnet, FTP) and replace with SSH/SFTP.
3. **Eliminate default and weak credentials**; enforce a password policy and lockout.
4. **Reduce attack surface**: close unused ports and apply host-based firewall rules.
5. **Upgrade the operating system** to a supported release and apply a patch-management process.

## Repository Structure

```
.
├── README.md
├── reports/network-vapt-report.md
├── findings/            # one file per finding
├── nmap/                # sanitized Nmap outputs
└── evidence/            # sanitized screenshots
```

## Disclaimer

For educational and portfolio use only. Never scan or exploit systems you do not own or have written permission to test.
