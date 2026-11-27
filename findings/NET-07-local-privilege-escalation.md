# NET-07: Local Privilege Escalation Path

> **High** · CVSS 3.1 base 7.8 · <!-- TODO: vector, e.g., SUID binary, kernel, misconfigured service --> · <!-- TODO: CVE if applicable -->

### What's wrong

A low-privileged account could escalate to root through <!-- TODO: vector -->.

### Reproducing it in the lab

1. From a low-privileged lab shell, enumerate the host (kernel version, SUID binaries, sudo rights, cron jobs).
2. Validate the escalation vector <!-- TODO: steps -->.
3. Confirm with `id` showing uid=0 <!-- TODO: evidence -->.

<!-- TODO: paste sanitized command output (IPs replaced with <TARGET_IP>) and link the screenshot from ../evidence/ -->

### Impact

Any initial foothold becomes full root compromise.

### Recommended fix

- Patch kernel and vulnerable packages.
- Remove unnecessary SUID bits and tighten sudo rules.
- Apply least privilege to services.
