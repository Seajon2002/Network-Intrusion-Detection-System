# 🛡️ Network Intrusion Detection System (NIDS) using Suricata on Kali Linux

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue)
![Tool](https://img.shields.io/badge/IDS-Suricata-red)
![Language](https://img.shields.io/badge/Scripting-Bash-green)
![Status](https://img.shields.io/badge/Project-Completed-success)

## 📌 Project Overview

This project demonstrates the implementation of a **Network Intrusion Detection System (NIDS)** using **Suricata** on Kali Linux.

The system continuously monitors network traffic, detects suspicious activities using custom detection rules, generates alerts in real-time, and implements a basic response mechanism using Linux Firewall (iptables).

This project was completed as part of my **Cyber Security Internship Program**.

---

## 🎯 Objectives

- Install and configure Suricata IDS
- Update Emerging Threats (ET) rules
- Create custom detection rules
- Detect network attacks in real time
- Monitor alerts using Suricata logs
- Simulate attacks using Nmap, Ping and SSH
- Block malicious IP addresses using iptables

---

## 🛠️ Technologies Used

- Kali Linux
- Suricata 8.0.5
- Nmap
- iptables
- Bash
- Nano Editor

---

## 📂 Project Structure

```
Network-Intrusion-Detection-System/

│── README.md
│── screenshots/
│── rules/
│      └── local.rules
│── scripts/
│      └── block_ip.sh
```

---

## ⚙️ Installation

Update packages

```bash
sudo apt update
sudo apt upgrade -y
```

Install Suricata

```bash
sudo apt install suricata -y
```

Check Version

```bash
suricata --build-info
```

Update Rules

```bash
sudo suricata-update
```

Start Service

```bash
sudo systemctl start suricata
```

Check Status

```bash
sudo systemctl status suricata
```

---

## 📝 Custom Rules

The following custom rules were implemented.

```text
alert icmp any any -> any any (msg:"Ping Detected"; sid:1000001; rev:1;)

alert tcp any any -> any 22 (msg:"SSH Connection"; sid:1000002; rev:1;)

alert tcp any any -> any 80 (msg:"HTTP Request"; sid:1000003; rev:1;)

alert tcp any any -> any any (flags:S; msg:"Possible Nmap SYN Scan"; sid:1000004; rev:1;)

alert tcp any any -> any 21 (msg:"FTP Connection"; sid:1000005; rev:1;)

alert tcp any any -> any 23 (msg:"Telnet Connection"; sid:1000006; rev:1;)

alert udp any any -> any 53 (msg:"DNS Query"; sid:1000007; rev:1;)
```

---

## 🚀 Attack Simulation

The following activities were generated to test the IDS.

- ICMP Ping
- SSH Connection
- HTTP Request
- Nmap Scan
- Nmap Aggressive Scan

Example:

```bash
ping 192.168.1.8

nmap 192.168.1.8

sudo nmap -A 192.168.1.8
```

---

## 🚨 Alert Detection

Suricata successfully detected

- ICMP Ping
- SSH Connection
- HTTP Requests
- Nmap Scan
- DHCP Events

Alerts were monitored using

```bash
sudo tail -f /var/log/suricata/fast.log
```

---

## 🛡️ Response Mechanism

A basic response mechanism was implemented using Linux Firewall.

```bash
sudo iptables -A INPUT -s 192.168.1.8 -j DROP
```

Verify Rule

```bash
sudo iptables -L
```

---

## 📸 Screenshots

### Suricata Installation

![Installation](screenshots/installation.png)

---

### Service Status

![Status](screenshots/status.png)

---

### Updating Rules

![Update](screenshots/update-rules.png)

---

### Custom Rules

![Rules](screenshots/local-rules.png)

---

### Attack Simulation

![Attack](screenshots/attack-simulation.png)

---

### Alerts

![Alerts](screenshots/alerts.png)

---

### Response Mechanism

![iptables](screenshots/iptables.png)

---

## ✅ Results

Successfully implemented a functional Network Intrusion Detection System capable of:

- Monitoring network traffic
- Detecting suspicious activities
- Generating alerts
- Detecting custom attack signatures
- Blocking attacker IP addresses

---

## 🔮 Future Improvements

- Integrate ELK Stack (Elasticsearch, Logstash, Kibana)
- Email alert notifications
- Automatic IP blocking using Suricata Eve JSON
- Web-based monitoring dashboard
- Integration with SIEM platforms

---

## 👨‍💻 Author

**Ektearul Haque**

B.Sc. in Software Engineering (Major: Cybersecurity)

GitHub: https://github.com/Seajon2002/

LinkedIn: https://www.linkedin.com/in/ektearulhaque/

---

## 📜 License

This project is released under the MIT License.
