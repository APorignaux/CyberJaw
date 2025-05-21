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

## 🧱 3D Printed Case & Assembly

This section explains how to print and assemble the CyberJaw hardware using the provided 3D-printed case files.

### 1. 🖨️ Printing the Case

You'll find all `.stl` files in the [`/3d_models/`](./3d_models/) directory for 3D printing the CyberJaw enclosure and its components.

You have two options for the main case:

- **Single-Part STL**  
  Use this version if you have time for a longer print. It results in a stronger, more durable case printed as one solid piece.

- **Multi-Part STL (Case + Separator)**  
  This version breaks the case into two parts: the main case and an internal separator. It prints faster and fits on smaller printers.  
  ➕ You'll need **super glue** to assemble both parts afterward.

Additionally, there's a small component called:

- **`switchON/OFF` Adapter**  
  This piece is designed to extend the physical on/off switch on the battery shield, which would otherwise be inaccessible once inside the case.  
  It looks like a small "crab claw" and is meant to fit over the existing shield switch.  
  ➤ After printing:
  1. Insert the part into its slot in the case.
  2. Gently glue it to the switch's protruding shaft.
  3. Once fixed, it lets you control power from outside the case.

### 2. 🧩 Assembling the Hardware

To mount the internal components:

- Use **3mm thick countersunk head bolts**.
- Cut them to about **4mm long** so they anchor into the plastic without poking through (which could cause short circuits).
- You can control the cut length by placing **two nuts on the bolt**, then trimming with a Dremel or file.

> ⚠️ Note: The mounting holes are intentionally slightly narrower than 3mm so the bolts stay firmly in place without wobbling.

### 3. 🔌 Power Supply Wiring

To power the Raspberry Pi via the battery shield:

1. Plug a regular USB cable into the USB output port on the shield.
2. Cut the **other end** of the USB cable to expose the **power wires** (typically red and black).
3. Solder each wire to individual jumper wires.
4. Use the table below to connect them correctly to the Pi’s GPIO power input pins.

| Wire Color | Function     | Connects To (GPIO Pin) |
|------------|--------------|------------------------|
| Red        | +5V Power    | Pin 2 or Pin 4         |
| Black      | Ground (GND) | Pin 6 or Pin 9         |

> Make sure to double-check polarity before powering on.


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

Here is the corresponding pins on the raspberry pi : [`/docs/resources/pins_dispositions.png`](./docs/resources/pins_dispositions.png)

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

## ⚙️ CyberJaw Technical Specifications & Power Management

This section outlines the hardware specifications, power efficiency, and charging guidelines for the CyberJaw device.

### 🔋 Power Supply & Efficiency

- **Battery Type**: 18650 Li-Ion cell (e.g., 3600mAh)
- **Battery Shield**: AZDelivery 18650 Battery Expansion Shield V3
- **Output Voltage**:
  - **5V/1A** via USB port
  - **3V/1A** via expansion pins
- **Conversion Efficiency**: Up to 95%
- **Idle Power Consumption**: ~97mA
- **Estimated Idle Runtime**: ~37 hours on a 3600mAh battery

> ⚠️ Note: Actual runtime may vary based on active tasks and environmental conditions.

### 🔌 Charging Guidelines

- **Input Voltage**: 5V DC (via Micro USB)
- **Recommended Charger**: 5V/1A USB power supply
- **Charging Current**: 500mA
- **Estimated Charging Time**: Approximately 7–8 hours for a 3600mAh battery

> ⚠️ Caution: Ensure correct polarity when inserting the battery to prevent damage.

### 📦 Hardware Components

- **Mainboard**: Raspberry Pi Zero 2W
- **Ethernet Module**: W5500 (operates at 3.3V)
- **Battery Shield**: AZDelivery 18650 Battery Expansion Shield V3
- **Battery**: 18650 Li-Ion cell (e.g., 3600mAh)
- **3D Printed Case**: Custom-designed enclosure with optional `switchON/OFF` adapter

### 🔧 Power Optimization Features

To enhance power efficiency:

- **CPU Frequency**: Reduced to 600MHz
- **Disabled Components**:
  - GPU
  - HDMI
  - Audio
  - Camera interface
  - Power LED

These optimizations are configured via the `config.txt` file. A pre-configured version is available at [`/docs/resources/config.txt`](./docs/resources/config.txt).

> 💡 Tip: Disabling unused components conserves battery life and reduces heat generation.

### 📈 Performance Summary

| Component           | Specification           |
|---------------------|-------------------------|
| CPU Frequency       | 600MHz                  |
| Idle Current Draw   | ~97mA                   |
| Battery Capacity    | 3600mAh                 |
| Estimated Idle Time | ~37 hours               |
| Charging Time       | ~7–8 hours              |
| Output Voltage      | 5V/1A (USB), 3V/1A (pins)|
| Ethernet Voltage    | 3.3V (W5500 module)     |

> 🔗 For more details on the AZDelivery 18650 Battery Expansion Shield V3, refer to the [official product page](https://www.az-delivery.de/en/products/battery-expansion-shield-18650-v3-inkl-usb-kabel).

---
## Future Enhancements

- Add Ethernet pass-through functionality.  
- Implement encrypted communication for data exfiltration.  
- Develop a dedicated web interface for remote control.  

---

## Disclaimer

> **CyberJaw is for educational and authorized security testing purposes only. Unauthorized use is illegal and unethical. Use responsibly.**
