# Network Pentest: Metasploitable 2

Metasploitable 2 is Rapid7's deliberately broken Linux VM. I set it up on a host-only network next to a Kali VM and worked through it end to end: discovery, enumeration, vulnerability scanning, exploitation, and a look around afterwards to see how far a foothold could go. This repo is the documented result.

> **Lab only.** Both VMs sat on a host-only virtual network with no route to the internet or my home network. Every exploit in this write-up was run against the Metasploitable VM and nothing else.

## The lab

```
 ┌────────────────────┐        host-only network        ┌──────────────────────┐
 │  Kali Linux        │  ─────────────────────────────▶ │  Metasploitable 2    │
 │  <ATTACKER_IP>     │   Nmap · Nessus · Metasploit    │  <TARGET_IP>         │
 └────────────────────┘                                 └──────────────────────┘
          no NAT, no bridged adapter, no internet access on either VM
```

I've replaced the real lab addresses with `<ATTACKER_IP>` and `<TARGET_IP>` everywhere in this repo.

## Toolkit

Nmap for discovery and service fingerprinting · Nessus for vulnerability scanning · Nikto for the web server · Netcat for banner grabbing and manual connections · Metasploit Framework for controlled exploitation.

## How it went

**1. Finding the host and its ports.** A ping sweep of the lab subnet, then a full TCP scan. Metasploitable answers on a *lot* of ports, which is the first sign of trouble: a real server should expose only what it needs.

**2. Working out what each service was.** `nmap -sC -sV` against the open ports, followed by manual banner grabs with Netcat where Nmap's guess looked uncertain. I also ran Nikto against the web server and SMB enumeration scripts against Samba. The sanitized outputs are in [`nmap/`](nmap/).

**3. Scanning for known vulnerabilities.** Nessus gave me a long list of findings. I cross-checked the critical ones against the service versions I had already identified, so I wasn't relying on the scanner alone.

**4. Exploiting what I'd validated.** I only attempted exploitation for issues I had confirmed, and only against this VM. Several unrelated paths led to a shell, which says a lot about how exposed the box is.

**5. Looking around after access.** Once I had a shell I checked who I was, what the system was, and whether a low-privileged user could become root.

## Findings

| ID | Issue | Severity | CVSS 3.1 |
|---|---|---|---|
| [NET-01](findings/NET-01-outdated-ftp-service.md) | FTP service running a version with a known critical flaw | 🔴 Critical | 9.8 |
| [NET-02](findings/NET-02-smb-remote-code-execution.md) | Samba version vulnerable to remote code execution | 🔴 Critical | 9.8 |
| [NET-03](findings/NET-03-weak-default-credentials.md) | Weak and default credentials on network services | 🟠 High | 8.8 |
| [NET-07](findings/NET-07-local-privilege-escalation.md) | Local privilege escalation to root | 🟠 High | 7.8 |
| [NET-06](findings/NET-06-outdated-unsupported-software.md) | End-of-life operating system and services | 🟠 High | 7.5 |
| [NET-04](findings/NET-04-cleartext-telnet.md) | Telnet used for remote administration | 🟠 High | 7.4 |
| [NET-05](findings/NET-05-insecure-ftp-configuration.md) | FTP allows cleartext and anonymous logins | 🟡 Medium | 5.3 |
| [NET-08](findings/NET-08-web-server-misconfiguration.md) | Web server misconfigurations flagged by Nikto | 🟡 Medium | 5.3 |

The full write-up, with an executive summary and remediation plan, is in [reports/network-vapt-report.md](reports/network-vapt-report.md).

## After getting in

<!-- TODO: fill in from your own notes -->
- **Access level reached:** <!-- TODO: e.g., root -->
- **What I checked:** kernel and OS version, local users and groups, SUID binaries, sudo rights, cron jobs, world-writable files
- **Privilege escalation:** see [NET-07](findings/NET-07-local-privilege-escalation.md)
- **Persistence:** deliberately not attempted; out of scope for this lab

## What I would fix first

1. **Patch or remove** the vulnerable FTP and Samba services. Either one alone gives remote root.
2. **Change every default password** and enforce a real password policy.
3. **Turn off Telnet and plain FTP** and use SSH/SFTP instead.
4. **Close what isn't needed.** Most of the open ports have no business being reachable.
5. **Move to a supported OS** and put patching on a schedule.

## Takeaways

- Enumeration did most of the work. Once I had accurate service versions, the exploitable issues were obvious.
- Nessus was good for coverage but needed checking. Matching its output to my own version data cut out the noise.
- Seeing several independent routes to root made the case for defence in depth far more clearly than any textbook.

## Layout

```
├── reports/network-vapt-report.md
├── findings/   one page per issue
├── nmap/       sanitized scan output
└── evidence/   sanitized screenshots
```

---
*Educational and portfolio use only. Never scan or exploit systems you don't own or have written permission to test.*
