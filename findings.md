# 🔍 Findings: ARP Spoofing Attack

## 🎯 Objective
Intercept traffic between a victim and router via ARP poisoning and demonstrate credential theft using MitM.

---

## 📊 Observations
- **Bettercap** successfully poisoned ARP tables.
- Victim unknowingly submitted credentials to a **fake website**.
- **Wireshark** confirmed plaintext credentials in HTTP traffic.

---

## 🧬 DNS Spoofing Findings

- Observed DNS request from victim for `web.mnsu.edu`
- Attacker sent forged DNS reply pointing to attacker's local IP
- Victim’s browser loaded attacker’s fake site (hosted via SEToolkit)
- Wireshark logs confirmed DNS response was **not from real DNS server**

### 📎 Wireshark Indicators

- TTL anomalies
- Unexpected authoritative source in DNS response
- Plaintext credentials in HTTP POST requests

---

## 🔐 Key Lessons

- DNS spoofing can be performed post-ARP poisoning if attacker is in the path
- DNSSEC could help prevent this in real-world scenarios

---

## 📉 Vulnerabilities Exploited
- ARP’s lack of authentication
- Insecure HTTP login page
- Lack of network segmentation or ARP protections

---

## 🛡️ Recommendations
- Enforce HTTPS + HSTS
- Deploy VLANs and DHCP Snooping
- Enable Dynamic ARP Inspection
- Train users to detect phishing
