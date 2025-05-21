
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

