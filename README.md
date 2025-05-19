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

## Hardware Setup

Before anything else, the wiring must be done correctly. Below is a table that shows how to connect the Raspberry Pi Zero W to the WIZ850io module:

| Raspberry Pi Zero W Pin | Function           | WIZ850io Pin |
|-------------------------|--------------------|--------------|
| 6                       | GND                | GND          |
| 1                       | 3.3V               | 3.3V         |
| 23                      | SPI0_SCLK          | SCLK         |
| 19                      | SPI0_MOSI          | MOSI         |
| 21                      | SPI0_MISO          | MISO         |
| 18                      | BCM 24             | RSTn         |
| 22                      | BCM 25             | INTn         |
| 24                      | SPI0_CE0           | SCNn         |

---

## Software Setup

1. **Flash the image into the CyberJaw**
   ## Flashing Kali Linux or Raspberry Pi OS Using Raspberry Pi Imager

    Follow these steps to flash an OS (such as Kali Linux or Raspberry Pi OS Lite) onto your Raspberry Pi Zero 2W using the **Raspberry Pi Imager**:
    
    ### 🧰 Requirements
    
    - Raspberry Pi Imager installed on your computer  
      → [Download here](https://www.raspberrypi.com/software/)
    - A microSD card (8GB minimum recommended)
    - A microSD card reader
    
    ---
    
    ### 🔧 Step-by-Step Instructions
    
    1. **Insert your microSD card**  
       Plug the card into your computer using a card reader.
    
    2. **Launch Raspberry Pi Imager**  
       Open the Raspberry Pi Imager application.
    
    3. **Choose the OS**  
       Click **"Choose OS"** and select:
       - For Kali Linux: Scroll down to **"Other specific-purpose OS" > "Kali Linux"**  
       - For Raspberry Pi OS Lite: Go to **"Raspberry Pi OS (other)" > "Raspberry Pi OS Lite (32-bit)"**
    
    4. **Choose the storage**  
       Click **"Choose Storage"** and select your microSD card.
    
    5. **(Important) Preconfigure settings**  
       Click the gear ⚙️ icon (or press `Ctrl+Shift+X`) to open **advanced options**:
       - Enable SSH
       - Set a hostname like CyberJaw
       - Set username and password  
       - Configure Wi-Fi credentials (network you'll use to stealth connect to the CyberJaw) 
       - Set locale (e.g., keyboard, time zone)
    
    6. **Write the OS**  
       Click **"Write"** to start flashing the image onto the SD card.  
       Confirm when prompted. This process may take several minutes.
    
    7. **Eject the card**  
       Once the flashing is complete and verified, safely eject the microSD card.
    
    8. **Insert into Raspberry Pi**  
       Plug the card into the Raspberry Pi Zero 2W and power it on.
    
    You can now connect to the Pi using SSH, if you configure the wifi credentials right the CyberJaw will automatically connect to your ad-hoc network,
   then you can connect to the CyberJaw by the cname (default: CyberJaw.local) you gave him :
   ```bash
   ssh userYouChoose@CyberJaw.local
   ```

    ---

## 2. Power Consumption Optimization

To conserve energy, we’ll disable several components that are unnecessary for CyberJaw’s operation.

### 🔧 Step-by-Step Instructions

1. **Access the SD Card**  
   After flashing the OS image to the SD card, insert it into your computer.  
   You will find a file named `config.txt` at the root of the boot partition. This file controls which hardware components are enabled and the CPU frequency settings.

2. **Edit `config.txt`**  
   Open the file in a text editor and modify it to reduce power consumption.

   You can download a pre-configured version here:  
   👉 [`/docs/resources/config.txt`](./docs/resources/config.txt)

   This configuration includes:
   - ✅ Lowering CPU frequency to **600MHz**
   - ✅ Disabling the **GPU**
   - ✅ Disabling the **power LED**
   - ✅ Disabling the **camera interface**
   - ✅ Disabling **HDMI**
   - ✅ Disabling **audio**

3. **Save and Reinsert the SD Card**  
   After saving the file, eject the SD card and insert it back into the Raspberry Pi.

4. **Boot with Optimized Settings**  
   On next boot, the Raspberry Pi will apply the new power-saving parameters automatically.

> These changes help extend battery life, especially when CyberJaw is idle or running lightweight tasks, expanding the battery life to a maximum of 37 hours idle(with a 3600mAh)

---
    
3. **Enable the W5500 driver**  
   Edit the bootloader configuration file:

   ```bash
   sudo nano /boot/firmware/config.txt
    ```
   Add the following line at the end:
   ```ini
   dtoverlay=w5500
   ```
   Then reboot the system:
   ```bash
   sudo reboot
    ```
   Load the driver module after reboot (Once SSH connection is re-established :) )
   ```bash
   sudo modprobe w5100_spi
   lsmod | grep w5100 
    ```
   Now check if the interface is up (eth0)
   ```bash
   ip a
    ```

   
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
