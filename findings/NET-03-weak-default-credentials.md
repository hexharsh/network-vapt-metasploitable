# NET-03: Weak or Default Credentials on Network Services

> **High** · CVSS 3.1 base 8.8 · <!-- TODO: services, e.g., SSH, FTP, database --> · no CVE (configuration issue)

### What's wrong

One or more services accepted weak or default username/password combinations.

### Reproducing it in the lab

1. Enumerate services that accept credentials.
2. Test a small, targeted wordlist against lab services only <!-- TODO: tool used -->.
3. Record successful logins (do not publish passwords) <!-- TODO: result -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Attackers could log in directly and pivot to further compromise.

### Recommended fix

- Change all default passwords.
- Enforce password complexity and account lockout.
- Prefer key-based authentication for SSH.
