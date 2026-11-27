# NET-06: Outdated and Unsupported Operating System and Services

> **High** · CVSS 3.1 base 7.5 · Host OS and multiple services · Multiple <!-- TODO: from Nessus -->

### What's wrong

The operating system and many services are end-of-life and no longer receive security updates.

### Reproducing it in the lab

1. Review Nessus results for end-of-life and missing-patch plugins <!-- TODO: plugin IDs -->.
2. Confirm versions with banner grabbing (Netcat) and Nmap `-sV`.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Large number of exploitable known vulnerabilities.

### Recommended fix

- Migrate to a supported OS release.
- Implement regular patch management.
- Remove unused services.
