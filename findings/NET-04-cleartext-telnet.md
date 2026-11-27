# NET-04: Cleartext Telnet Remote Administration

> **High** · CVSS 3.1 base 7.4 · 23/tcp Telnet · no CVE (configuration issue)

### What's wrong

Telnet transmits credentials and session data in cleartext.

### Reproducing it in the lab

1. Confirm Telnet is open (`nmap -sV -p 23 <TARGET_IP>`).
2. Capture a lab login with Wireshark/tcpdump and observe cleartext credentials <!-- TODO: result, values redacted -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Anyone on the network path can capture administrator credentials.

### Recommended fix

- Disable Telnet.
- Use SSH with key-based authentication.
