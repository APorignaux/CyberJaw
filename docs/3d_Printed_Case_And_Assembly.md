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

![Case Part 1](../Images/Case1.jpeg)
![Case Part 2](../Images/Case2.jpeg)
![Case Assembled](../Images/Case3.jpeg)

Additionally, there's a small component called:

- **`switchON/OFF` Adapter**  
  This piece is designed to extend the physical on/off switch on the battery shield, which would otherwise be inaccessible once inside the case.  
  It looks like a small "crab claw" and is meant to fit over the existing shield switch.  
  ➤ After printing:
  1. Insert the part into its slot in the case.
  2. Gently glue it to the switch's protruding shaft.
  3. Once fixed, it lets you control power from outside the case.

![Glued ON/OFF Extension](../Images/glued_ON:OFF_extentsion.jpeg)

---

### 2. 🧩 Assembling the Hardware

To mount the internal components:

- Use **3mm thick countersunk head bolts**.
- Cut them to about **4mm long** so they anchor into the plastic without poking through (which could cause short circuits).
- You can control the cut length by placing **two nuts on the bolt**, then trimming with a Dremel or file.

> ⚠️ Note: The mounting holes are intentionally slightly narrower than 3mm so the bolts stay firmly in place without wobbling.

🪚 **Important Fit Tip**  
Before assembling the lid and box:

- Lightly **sand the inner edges** where the lid and the case meet using **160 grit sandpaper**.
- This smooths out any irregularities and slightly **chamfers the corners**, making it much easier to open and close the case.
- Don’t over-sand! A small adjustment is enough — too much, and the lid may no longer hold tightly.

![Smooth Corner Sanding](../Images/smooth_corner_and_glued_switch.jpeg)

---

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

> 🔋 Make sure to double-check polarity before powering on.

![Power Wiring](../Images/wired_ethernet.jpeg)

---

### 4. 🧲 Stealth Magnet Mounting (Optional, But Cool)

For improved stealth deployment, you can **magnetize the CyberJaw case** to discreetly attach it under a switch, desk, or any metal surface:

- Glue a **strong magnet** inside the upper wall of the printed case (on the side that will face upward during mounting).
- An old **hard disk drive (HDD) magnet** works great — powerful, flat, and easy to find.
- The device can then cling to metal surfaces securely and remain **virtually unnoticed**, especially if installed in tight or shadowed areas.

![Glued Magnet](../Images/glued_magnet.jpeg)
![Powered Up Project](../Images/Powered_up_Project.jpeg)

---
