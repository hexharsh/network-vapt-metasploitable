# Evidence

Add **sanitized** screenshots here. Name files `<FINDING-ID>-<description>.png`.

## Redaction Rules

- [ ] Replace lab IP addresses with `<ATTACKER_IP>` / `<TARGET_IP>` (blur in screenshots)
- [ ] Remove hostnames and usernames of your own physical machine
- [ ] Do not show cracked password values; write `[REDACTED]`
- [ ] Crop out unrelated windows and notifications

## Suggested Screenshots

| File | What it should show |
|---|---|
| `recon-nmap-full-scan.png` | Nmap full port and service scan summary |
| `nessus-summary.png` | Nessus severity summary for the target |
| `NET-01-exploit-result.png` | Exploit module options (IPs blurred) and resulting session |
| `NET-02-smb-exploit.png` | SMB exploitation result |
| `NET-03-weak-credentials.png` | Successful login with weak credentials (password redacted) |
| `NET-04-telnet-cleartext.png` | Cleartext login visible in a packet capture (values redacted) |
| `NET-07-privesc.png` | `id` output before and after privilege escalation |
| `NET-08-nikto.png` | Nikto output highlights |
