# Kioptrix Level 1 — Network Security Assessment

An individual network security project conducted against Kioptrix Level 1, an intentionally vulnerable Linux VM. Kali Linux and Kioptrix ran on the same VirtualBox NAT network (`10.10.10.0/24`).

## Methodology and findings

| Phase | Tools | Result |
| --- | --- | --- |
| Lab setup | VirtualBox, Kali Linux | Verified connectivity to Kioptrix at `10.10.10.4`. |
| Reconnaissance | Nmap | Identified six open TCP ports: 22, 80, 111, 139, 443, and 32768. |
| Traffic analysis | Wireshark | Reconstructed an HTTP exchange and inspected its plaintext contents. |
| Exploitation and password auditing | Metasploit, John the Ripper | Exploited Samba's `trans2open` vulnerability over TCP port 139 and obtained a root shell. Tested three MD5-crypt hashes using two wordlists and recovered zero passwords. |
| Security analysis | Assessment report | Documented weaknesses and proposed remediation. |

## Recommended remediation

- **Vulnerable Samba and outdated services** — Upgrade to supported versions and apply security patches.
- **Plaintext HTTP** — Use HTTPS with modern TLS for web traffic.
- **Legacy password hashing** — Migrate MD5-crypt hashes to a modern, supported password-hashing scheme.
- **Service exposure** — Disable unused services and restrict access to SMB and administrative services with firewall rules.

The assessment covered one training VM. The proposed mitigations were documented for future validation.

## Report

[Download the assessment report and lab screenshots](report/kioptrix-level1-security-assessment.docx).

## Scope

All testing took place in a controlled virtual lab for educational purposes.
