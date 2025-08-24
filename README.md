# SniffGuard 🛡️
*A lightweight, command-line Intrusion Detection System with a live dashboard & PCAP evidence capture.*

This is a project I built to deepen my understanding of data communications and cybersecurity. It's a lightweight IDS written in Python that monitors live network traffic, detects suspicious SYN-based port scans, logs alerts, and saves raw packet evidence for forensic analysis.

---
## ✨ Key Features
* **Live Dashboard:** Real-time traffic display using the Rich library.
* 🛡️ **SYN Scan Detection:** A robust, stateful engine to detect SYN-based port scans.
* **PCAP Evidence:** Saves all packets from a detected scan to a `.pcap` file for analysis in tools like Wireshark.
* **Dynamic & Robust:** Automatically detects available interfaces, uses efficient BPF filters, and handles errors gracefully.
* **Professional Logging:** Alerts are saved to a rotating log file to prevent disk space issues.
* **Fully Configurable:** All parameters (interfaces, thresholds, etc.) can be controlled via CLI arguments.

---

### 🖼️ Showcase
| Normal Monitoring | Alert Triggered |
| :---: | :---: |
| ![Normal Terminal](https://github.com/user-attachments/assets/3b942c29-8003-4ccf-bdca-dc30c8913276) | ![Alert Terminal](https://github.com/user-attachments/assets/7eed5f88-d8f2-49d0-8928-b2b7fe3b773d) |

---

### ✅ Prerequisites
* Python 3.8+
* Root/Administrator privileges to run.
* On Windows, [Npcap](https://npcap.com/) must be installed.

---

## 🚀 Quick Start

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/BarDev1999/SniffGuard.git](https://github.com/BarDev1999/SniffGuard.git)
    cd SniffGuard
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the IDS:**
    ```bash
    # On Linux/macOS
    sudo python3 sniffer_proj.py
    ```

---

## ⚙️ Lab Demo Commands
You can test the IDS safely in your lab environment with these commands:

```bash
# Nmap Scan (targets ports 1-200 on localhost)
sudo nmap -sS -p 1-200 127.0.0.1

# Hping3 Scan (sends 120 SYN packets to incrementing ports starting from 80)
sudo hping3 -S --flood --rand-source -p ++80 -c 120 127.0.0.1
```

---

## 📜 License
This project is licensed under the MIT License.
