## 🧠 Hardware Setup

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

🖼️ **Raspberry Pi Pin Layout:**  
[Pin Dispositions](../ressources/Images/pins_dispositions.png)

---

## 💾 Software Setup

### 1. Flash the image into the CyberJaw

#### 🖥️ Flashing Kali Linux or Raspberry Pi OS Using Raspberry Pi Imager

Follow these steps to flash an OS (such as Kali Linux or Raspberry Pi OS Lite) onto your Raspberry Pi Zero 2W using the **Raspberry Pi Imager**:

#### 🧰 Requirements

- Raspberry Pi Imager installed on your computer  
  → [Download here](https://www.raspberrypi.com/software/)
- A microSD card (8GB minimum recommended)
- A microSD card reader

---

#### 🔧 Step-by-Step Instructions

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
   - Set a hostname like `CyberJaw`
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

You can now connect to the Pi using SSH. If you configure the Wi-Fi credentials correctly, the CyberJaw will automatically connect to your ad-hoc network, and you can connect by the hostname (default: `CyberJaw.local`):

```bash
ssh userYouChoose@CyberJaw.local
