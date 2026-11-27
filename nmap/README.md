# Nmap output

Sanitized scan output from the lab. Real addresses are replaced with `<TARGET_IP>` / `<ATTACKER_IP>`.

## Commands I ran

```bash
# Host discovery on the isolated lab network
nmap -sn <LAB_SUBNET>

# Full TCP port scan
nmap -p- -T4 -oA nmap/01-full-tcp <TARGET_IP>

# Service and version detection with default scripts
nmap -sC -sV -p <OPEN_PORTS> -oA nmap/02-service-version <TARGET_IP>

# Vulnerability-focused NSE scripts
nmap --script vuln -p <OPEN_PORTS> -oA nmap/03-vuln-scripts <TARGET_IP>

# SMB enumeration
nmap --script smb-os-discovery,smb-enum-shares,smb-enum-users -p 139,445 -oA nmap/04-smb-enum <TARGET_IP>
```

## How I sanitize output before committing

```bash
# Replace your real lab IPs before committing (example)
sed -i 's/<YOUR_REAL_TARGET_IP>/<TARGET_IP>/g; s/<YOUR_REAL_ATTACKER_IP>/<ATTACKER_IP>/g' nmap/*.nmap nmap/*.xml nmap/*.gnmap
grep -E '([0-9]{1,3}\.){3}[0-9]{1,3}' nmap/* && echo "IPs still present, review before committing"
```

<!-- TODO: add 01-full-tcp.nmap, 02-service-version.nmap, 03-vuln-scripts.nmap, 04-smb-enum.nmap -->
