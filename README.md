# 🐍 Python SYN IDS 🚦
*A minimal Intrusion Detection System (IDS) with a live dashboard & PCAP evidence*

This project is a lightweight IDS written in Python.
It monitors live network traffic, detects suspicious SYN-based port scans, logs alerts, and saves raw packet evidence for later analysis.

---
## ✨ Features
* **Real-time detection** of SYN flood & port scanning attempts
* **Live dashboard** with Rich (interactive console table)
* **Rotating logs** (`ids_alerts.log`) with severity levels
* **PCAP evidence files** saved automatically in `evidence/`
* **Configurable via CLI** – no need to edit the code

---
## 🚀 Quick Start

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR-USERNAME/sniffer-ids.git](https://github.com/YOUR-USERNAME/sniffer-ids.git)
    cd sniffer-ids
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the IDS** (example on loopback interface):
    ```bash
    sudo python3 sniffer_proj.py --interfaces lo --log-level info
    ```

4.  **(Optional) Simulate an attack in another terminal

To test the IDS, you can use nmap to generate port scan traffic. Here are two common examples:

Example A: Internal Scan (testing the lo interface)
Run this command from a terminal inside the VM.

Bash

sudo nmap -sS -p 1-1024 127.0.0.1
Example B: External Scan (testing the external interface)
Run this command from your host machine or another computer on the network.

Bash

nmap -sS -Pn <VM_IP_ADDRESS>
(Replace <VM_IP_ADDRESS> with your VM's actual network IP, such as 192.168.71.3)

---
## ⚙️ CLI Options

| Flag / Option              | Description                                                      | Example                               |
| -------------------------- | ---------------------------------------------------------------- | ------------------------------------- |
| `--interfaces`             | List of interfaces to monitor.                                   | `--interfaces lo enp0s3`              |
| `--port-scan-threshold`    | SYN packets within the time window to trigger an alert.          | `--port-scan-threshold 15`            |
| `--time-window-seconds`    | Sliding time window (seconds) for scan detection.                | `--time-window-seconds 10`            |
| `--alert-cooldown-seconds` | Cooldown before the same IP can trigger another alert.           | `--alert-cooldown-seconds 30`         |
| `--log-level`              | Logging verbosity (info = normal, debug = verbose).              | `--log-level debug`                   |

---
## 📂 Project Structure
```
SnifferProject/
├── sniffer_proj.py       # Main IDS script
├── requirements.txt      # Python dependencies
├── .gitignore            # Ignore cache, venv, logs, evidence
├── README.md             # Project documentation
├── LICENSE               # MIT License
└── evidence/             # PCAP evidence files (auto-created)
```

---
## 🔍 Example Output

**Normal monitoring (no alerts):**
```
[*] Starting IDS v2.0 (Self-Healing & Robust)...
[*] Monitoring interfaces: lo
[*] Press Ctrl+C to stop.
Live Network Traffic Dashboard (Monitoring: lo) 🚦
Status: Monitoring... All clear.
```

**When a port scan is detected:**
```
[*] Last Alert (21:30:12): PORT SCAN from 127.0.0.1. Evidence saved to evidence/scan...
```

---
## 🛠️ Requirements
* Python 3.10+
* scapy
* rich
* (optional) `nmap` or `hping3` for testing

---
## 📜 License
MIT License — feel free to use, modify, and share, but please keep attribution.

---
## 💡 About
This project was built as a hands-on learning project in Python, Networking, and Cybersecurity fundamentals. It’s intentionally minimal but designed to be extended (e.g., support for IPv6, detection of FIN/NULL/XMAS scans, etc.).
