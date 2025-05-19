#CyberJaw - Hotplug Network Attack Device
Overview
CyberJaw is a custom-built, compact network attack device inspired by the Shark Jack, leveraging a Raspberry Pi Zero 2W. Designed for red team engagements and network security assessments, CyberJaw can be discreetly plugged into a network for reconnaissance and exploitation.
Features

Hotplug Attack Capability – Auto-runs payloads upon connection.
Network Recon & Exploitation – Executes nmap scans, packet captures, and automated attack scripts.
Customizable Payloads – Runs Bash, Python, or custom scripts.
Wireless Connectivity – Uses Wi-Fi for remote control if needed.
Hardware Requirements

Raspberry Pi Zero 2W
Ethernet cable
W5500 Ethernet module
18650 Battery and shield
Software Setup

Flash Raspberry Pi OS (Lite) or Kali Linux
Enable SSH & Networking
Install Necessary Packages
<span>sudo apt update && sudo apt install nmap tcpdump dnsutils python3</span>

Create Auto-Execution ScriptsExample: payload.sh
<span>#!/bin/bash
ifconfig eth0 up
nmap -sP 192.168.1.0/24 > /tmp/scan_results.txt</span>

Set it to run automatically on connection using systemd or cron.
Usage

Plug CyberJaw into a target network.
It will automatically execute reconnaissance and attack scripts.
Retrieve results via SSH through ad-hoc connection.
Future Enhancements

Add Ethernet pass-through functionality.
Implement encrypted communication for data exfiltration.
Develop a dedicated web interface for remote control.
Disclaimer
CyberJaw is for educational and authorized security testing purposes only. Unauthorized use is illegal and unethical. Use responsibly.
