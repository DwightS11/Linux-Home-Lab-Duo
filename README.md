# NH-SS-Home-Lab

Documenting my dual-machine home lab setup (Linux + Windows 11) for cybersecurity practice, hands-on networking, and CompTIA Security+ prep.

---

## Machines

| Nickname | Model | CPU | OS | Role |
|----------|-------|-----|----|------|
| Nighthawk (NH) | Lenovo IdeaPad Flex 5 14ITL05 | 11th Gen Intel i3-1115G4 | Ubuntu 24.04 LTS | Linux lab machine |
| Silver Surfer (SS) | HP Envy m6-aq103dx | 7th Gen i5-1135G7 | Windows 11 | Windows lab machine |

---

## Goals

- Build a dual-OS home lab for cybersecurity practice
- Gain hands-on bare metal Linux and Windows experience
- Learn cross-platform networking and troubleshooting
- Set up a VPN between machines for secure communication
- Study for and pass CompTIA Security+
- Document everything for a professional portfolio

---

## Progress

- [x] Create bootable Ubuntu 24.04 USB
- [x] Install Ubuntu 24.04 on Nighthawk (bare metal)
- [x] Complete Windows reset on Silver Surfer
- [x] Upgrade Silver Surfer to Windows 11
- [x] Post-install configuration on Nighthawk (Ubuntu)
- [x] Harden security settings on both machines
- [x] Set up SSH between machines
- [x] Establish WireGuard VPN between Nighthawk and Silver Surfer
- [ ] Install and configure cybersecurity tools
- [ ] Set up Wireshark and analyze lab traffic
- [ ] Set up a SIEM

---

## Log

### Day 1
- Cancelled planned Windows reset on Nighthawk — going straight to Linux
- Downloaded Ubuntu 24.04.2 LTS (Noble Numbat)
- Created GitHub repo to document process
- Successfully installed Ubuntu 24.04 on Nighthawk (bare metal)
- Completed Windows reset on Silver Surfer
- Revised lab goals — dedicated OS per machine, no dual boot

### Day 2
- Successfully upgraded Silver Surfer to Windows 11
  - Used registry workaround (`AllowUpgradesWithUnsupportedTPMOrCPU`) due to AMD A10-9620P not meeting official TPM 2.0 requirements
- Removed McAfee and bloatware from Silver Surfer post-install
- Ran full system updates on both machines (`apt upgrade` on NH, Windows Update on SS)
- Configured login password on Nighthawk (modified PAM config to allow shorter password via `pam_pwquality.so minlen`)
- Installed and enabled UFW firewall on Nighthawk
  - Set default rules: deny incoming, allow outgoing
- Enabled unattended-upgrades on Nighthawk for automatic security updates
- Hardened Windows Security on Silver Surfer
  - Enabled reputation-based app/download protection
  - Confirmed Firewall on all three profiles (Domain/Private/Public)
  - Confirmed Core Isolation, Secure Boot, and Device Encryption active
- Installed OpenSSH server on Nighthawk
  - Opened SSH port through UFW
  - Successfully established SSH session from Silver Surfer → Nighthawk
- Installed and configured WireGuard VPN on both machines
  - NH configured as server (`10.0.0.1`), SS configured as client (`10.0.0.2`)
  - Generated key pairs on both machines
  - Configured inbound firewall rules on SS for UDP 51820 and ICMPv4
  - Verified bidirectional encrypted tunnel with successful ping both directions

---

## Roadmap

- [ ] Set up Wireshark — capture and analyze VPN traffic between NH and SS
- [ ] Practice firewall rule writing (UFW on NH, Windows Defender on SS)
- [ ] Nmap scanning between machines — enumerate open ports
- [ ] Set up a SIEM (Splunk Free or Security Onion)
- [ ] SSH hardening on NH — disable root login, key-based auth only
- [ ] Vulnerability scanning with OpenVAS
- [ ] Document Security+ study notes in this repo

---

*Student project — BSCyS @ University of South Florida | Targeting CompTIA Security+*
