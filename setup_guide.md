# ⚙️ ARP Spoofing Lab Setup Guide

## Tools Needed
- Kali Linux (Attacker)
- Windows 10 or Ubuntu (Victim)
- VirtualBox or VMware
- Internet disconnected (use Host-Only/IntNet)

## Configuration
1. Ensure both attacker and victim are on the same virtual network.
2. Confirm connectivity: `ping <victim IP>` from Kali.
3. Use `nmap` to scan the subnet and identify hosts.
4. Launch Bettercap to spoof ARP tables.
5. Use SEToolkit to host a fake login page.
6. Capture and analyze traffic in Wireshark.

## Notes
- Only use lab environments.
- Restart ARP tables with `arp -d` if needed.
