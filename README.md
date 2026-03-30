# Personal-Firewall
# Personal Firewall Using Python

[cite_start]This project presents a lightweight Personal Firewall implemented entirely in Python[cite: 1, 5]. [cite_start]It acts as both a command-line and GUI-based security tool, offering capabilities comparable to commercial personal firewall products while remaining fully transparent and extensible[cite: 3, 7].

## 🛡️ Core Features
* [cite_start]**Packet Sniffing:** Intercepts live network traffic using the Scapy library[cite: 6].
* [cite_start]**Rule Engine:** Evaluates each packet against a JSON-backed, configurable rule set based on IP addresses, ports, and protocols (ALLOW/BLOCK)[cite: 6, 21].
* [cite_start]**System-Level Enforcement:** Optionally integrates with Linux `iptables` for kernel-level packet filtering, independent of the Python process[cite: 7, 28].
* [cite_start]**Audit Logging:** Logs suspicious activity (like ICMP floods or port scans) to a structured `firewall.log` file[cite: 6, 24].
* [cite_start]**Real-Time Dashboard:** A graphical dashboard (HTML/JS) that displays a live packet feed, traffic statistics charts, rule management, and an auto-refreshing audit log[cite: 6, 29].

## 🛠️ Tech Stack
* [cite_start]**Core Language:** Python 3.10+ [cite: 14]
* [cite_start]**Network Manipulation:** Scapy 2.5+ [cite: 14]
* [cite_start]**System Filtering:** Linux kernel `iptables` / `python-iptables` [cite: 14]
* [cite_start]**Dashboard / GUI:** Tkinter / HTML+JS [cite: 14]
* [cite_start]**Background Processing:** Python `threading` library for non-blocking sniffing alongside the GUI [cite: 14]

## 📝 Project Architecture
[cite_start]The firewall is built with a modular architecture to ensure each component is independently testable and replaceable[cite: 12]. 
1. [cite_start]**Sniffer:** Uses Scapy's `sniff()` function with a background thread to capture inbound/outbound IP packets[cite: 20].
2. [cite_start]**Analysis:** The rule engine evaluates rules top-to-bottom, defaulting to ALLOW if no match is found[cite: 22].
3. [cite_start]**Action:** Blocked or suspicious packets are written to the audit log with timestamps, protocols, and matched rules[cite: 24].

> [cite_start]**Note:** The HTML file in this repository serves as the frontend GUI dashboard for live monitoring[cite: 12]. [cite_start]To run the actual packet interception, the Python backend (utilizing Scapy and iptables) must be executed with root/sudo privileges on a Linux environment[cite: 19, 28].
