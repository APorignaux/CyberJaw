# 🦈 CyberJaw – Hotplug Network Attack Device

> **A compact, plug-and-play cyber tool for red teams and pentesters.**

---

## 🚀 Overview

**CyberJaw** is a stealthy, Raspberry Pi Zero 2W–based network attack device inspired by the [Shark Jack](https://hak5.org/products/shark-jack). Built for red team operations and network reconnaissance, CyberJaw discreetly plugs into a network and immediately begins scanning, sniffing, or launching scripted payloads.

Whether you're auditing network infrastructure or simulating insider threats, CyberJaw provides a pocket-sized edge.

---

## 🛠️ Setup Guide

To get started, follow these step-by-step guides:

1. 🧱 [3D Printed Case & Hardware Assembly](./docs/resources/3d_Printed_Case_And_Assembly.md)  
2. 🧩 [Hardware & Software Setup](./docs/resources/Hardware_And_Software_Setup.md)  
3. 🔋 [Technical Specs & Charging Instructions](./docs/resources/Technical_Specs_And_Charging_Instructions.md)

---

## ✨ Features

- 🔌 **Hotplug Execution** – Automatically executes attack payloads upon network connection.
- 🔍 **Network Recon & Exploitation** – Performs stealthy scans (`nmap`), packet captures (`tcpdump`), and more.
- 🧠 **Custom Payload Support** – Bash, Python, or any script you want—fully customizable.
- 📡 **Remote Wireless Access** – Connect over Wi-Fi when physical access is no longer needed.

---

## 📦 Hardware Requirements

To build your own CyberJaw, you’ll need:

- 🧠 Raspberry Pi Zero 2W  
- 🌐 W5500 Ethernet Module  
- 🔌 Ethernet Cable  
- 🔋 18650 Li-Ion Battery + Shield  
- 🖨️ 3D Printed Case (optional, but recommended)

---

## ⚡ Usage

1. Plug CyberJaw into the target network.
2. Payloads execute automatically.
3. Access CyberJaw via SSH to exfiltrate results or trigger remote scripts.

---

## 🧪 Future Enhancements

- ⚡ Add Power Over Ethernet (PoE) capability  
- 🛡️ Encrypted VPN-based C2 (Command & Control) communications  
- 🌐 Web interface for visual payload management  

---

## ⚠️ Disclaimer

> CyberJaw is intended **only** for educational purposes and **authorized security testing**.  
> **Never use this device on networks without explicit permission.** Unauthorized use is **illegal and unethical**.  
> Use responsibly. 💻🔐

---

## 📚 Credits & Sources

- Power Consumption Data: [CNX Software – RPi Zero 2 W Power Tests](https://www.cnx-software.com/2021/12/09/raspberry-pi-zero-2-w-power-consumption/)
- Inspired by the [Shark Jack](https://hak5.org/products/shark-jack) by Hak5
