# NET-02: SMB Service Vulnerable to Remote Code Execution

> **Critical** · CVSS 3.1 base 9.8 · 139/445 tcp Samba <!-- TODO: version --> · <!-- TODO: CVE -->

### What's wrong

The Samba version in use is affected by a known vulnerability allowing remote code execution.

### Reproducing it in the lab

1. Enumerate SMB with Nmap NSE scripts (`smb-os-discovery`, `smb-enum-shares`).
2. Confirm version and vulnerability with Nessus <!-- TODO: plugin ID -->.
3. Exploit in the lab with <!-- TODO: module -->.
4. Record resulting access <!-- TODO: result -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Full system compromise from the network.

### Recommended fix

- Patch Samba to a supported version.
- Disable SMBv1 and unnecessary shares.
- Restrict SMB to trusted internal hosts.
