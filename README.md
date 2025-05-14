# 🛡️ ARP Spoofing: Man-in-the-Middle Attack Simulation

## 📚 Overview
This is a cybersecurity project simulating an **ARP Spoofing** (ARP Poisoning) attack in a controlled lab setup. The attacker inserts themselves between two communicating devices (victim and gateway) to intercept or manipulate traffic.

> ⚠️ This was done in a **virtual lab environment** for educational purposes only. All actions were performed ethically and legally.

---

## 👨‍💻 Contributors
- Ajay  
- Eros  
- Swoyam Bista

---

## 🧰 Tools Used
- [Bettercap](https://www.bettercap.org/) – ARP Spoofing & MitM
- [Wireshark](https://www.wireshark.org/) – Packet analysis
- [Nmap](https://nmap.org/) – Network scanning
- [SEToolkit](https://tools.kali.org/information-gathering/setoolkit) – Fake login page for credential theft

---

## 🖥️ Attack Scenario

### 💡 Step 1: Discover the Network
```bash
sudo nmap -O 192.168.1.0/24
```
📌 **Goal**: Find all live hosts and their OS information.

![Nmap Scan](images/nmap_scan_example.png)

---

### 💡 Step 2: ARP Spoofing (Bettercap)
Use Bettercap to poison ARP tables and redirect traffic.
```bash
sudo bettercap -T 192.168.1.200 --gateway 192.168.1.1
```

![Bettercap](images/bettercap_attack_flow.png)

---

### 💡 Step 3: Launch Fake Website (SEToolkit)
Victim visits a **fake login page** created using SEToolkit:
```
REAL: https://web.mnsu.edu/eservices  
FAKE: http://192.168.1.200/
```

![Fake Login](images/setoolkit_fake_login.png)

---

### 💡 Step 4: DNS Spoofing & Packet Capture

After ARP poisoning, the attacker injected a **fake DNS response** to redirect the victim to a malicious site (hosted using SEToolkit).

- The victim typed a real domain: `https://web.mnsu.edu`
- The attacker redirected it to: `http://192.168.1.200` (attacker’s fake login)

Captured DNS spoofing activity in Wireshark:

![DNS Spoofing Packet](images/wireshark_dns_spoof.png)

---

## 🔐 Prevention Techniques
- Enforce **HTTPS** with HSTS
- Implement **Multi-Factor Authentication (MFA)**
- Monitor networks with IDS (Snort, Suricata)
- Use **static ARP entries** or enable **Dynamic ARP Inspection**
- Educate users about phishing risks

---

## 📄 Documentation
- `setup_guide.md` – VM and tool configuration
- `findings.md` – Attack flow and analysis

---

## 🔒 Ethical Disclaimer
This project was conducted in a **controlled environment** with virtual machines. It is meant **solely for educational and ethical purposes**. Never attempt to perform ARP spoofing or any unauthorized activity on real networks.

---

## 🙋 About Me
**Swoyam Bista**  
Student | Security+ Candidate | Cybersecurity Enthusiast  
[LinkedIn](https://www.linkedin.com/) *(insert your real link)*
