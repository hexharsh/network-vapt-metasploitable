# NET-05: Insecure FTP Configuration

> **Medium** · CVSS 3.1 base 5.3 · 21/tcp FTP · no CVE (configuration issue)

### What's wrong

FTP allows cleartext authentication and/or anonymous access.

### Reproducing it in the lab

1. Run `nmap --script ftp-anon -p 21 <TARGET_IP>`.
2. Attempt anonymous login <!-- TODO: result -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Data exposure and credential sniffing.

### Recommended fix

- Disable anonymous login.
- Replace FTP with SFTP or FTPS.
