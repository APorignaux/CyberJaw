# CyberJaw - Hotplug Network Attack Device

## Overview

**CyberJaw** is a custom-built, compact network attack device inspired by the Shark Jack, leveraging a Raspberry Pi Zero 2W. Designed for red team engagements and network security assessments, CyberJaw can be discreetly plugged into a network for reconnaissance and exploitation.

---

## Features

- 🔌 **Hotplug Attack Capability** – Auto-runs payloads upon connection.  
- 🔍 **Network Recon & Exploitation** – Executes `nmap` scans, packet captures, and automated attack scripts.  
- ⚙️ **Customizable Payloads** – Runs Bash, Python, or custom scripts.  
- 📶 **Wireless Connectivity** – Uses Wi-Fi for remote control if needed.  

---

## Hardware Requirements

- Raspberry Pi Zero 2W  
- W5500 Ethernet module  
- Ethernet cable  
- 18650 Battery and shield

---
   
## Usage

1. Plug CyberJaw into a target network.
2. It will automatically execute reconnaissance and attack scripts.
3. Retrieve results via SSH through an ad-hoc Wi-Fi connection.

---
## Future Enhancements

- Add Ethernet pass-through functionality.  
- Implement encrypted communication for data exfiltration.  
- Develop a dedicated web interface for remote control.  

---

## Disclaimer

> **CyberJaw is for educational and authorized security testing purposes only. Unauthorized use is illegal and unethical. Use responsibly.**
