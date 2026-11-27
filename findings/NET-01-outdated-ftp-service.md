# NET-01: Outdated FTP Service with Known Critical Vulnerability

> **Critical** · CVSS 3.1 base 9.8 · 21/tcp FTP <!-- TODO: version --> · <!-- TODO: CVE -->

### What's wrong

The FTP service runs a version with a publicly known vulnerability that can lead to remote command execution.

### Reproducing it in the lab

1. Identify version with `nmap -sV -p 21 <TARGET_IP>`.
2. Correlate the version with Nessus results / public advisories <!-- TODO: CVE -->.
3. Exploit in the lab with <!-- TODO: Metasploit module or manual technique -->.
4. Confirm access level with `id` <!-- TODO: result -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Remote, unauthenticated attacker could execute commands on the host.

### Recommended fix

- Upgrade to a supported, patched FTP server or remove the service.
- Restrict access with a host firewall.
- Monitor for unexpected listening ports.
