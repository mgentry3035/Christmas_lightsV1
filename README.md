# Christmas_lightsV1
# 🎄 Bluetooth-Controlled Christmas Lights (Arduino Project)

## 📘 Overview
This project lets you control colorful Christmas lights from your **mobile phone** over **Bluetooth**.  
Using an **Arduino** and a **Bluetooth module (HC-05 or HC-06)**, you can turn lights **on/off**, **change colors**, and **trigger flashing or fading patterns** — all from a simple Bluetooth terminal app.

> **Goal:** Learn how to integrate embedded control, Bluetooth communication, and light animations in one system.

---

## 🧠 Features
- 🔵 **Bluetooth control** using any Android Bluetooth terminal app  
- 🌈 **Multiple color options** (using RGB or addressable LED strips like WS2812)  
- ✨ **Light patterns** — flashing, fading, color chasing, etc.  
- 💡 **Continuous operation** (powered from wall or external DC supply)  
- ⚙️ **Modular code structure** — easy to expand for more patterns or automation  

---

## 🧰 Hardware Requirements

| Component | Description | Example |
|------------|--------------|----------|
| **Arduino Board** | Any standard Arduino (Uno, Nano, Mega, etc.) | Arduino Uno R3 |
| **Bluetooth Module** | For wireless serial communication | HC-05 or HC-06 |
| **LEDs** | Either: analog RGB strip (3 PWM pins) or addressable LEDs | WS2812 / NeoPixel strip |
| **Transistor / Relay / MOSFET Board** | To safely switch lights | Logic-level MOSFETs (IRLZ44N, AO3400A, etc.) |
| **Power Supply** | 5V or 12V, depending on your lights | 5V/10A DC adapter |
| **Jumper Wires / Breadboard / Connectors** | For wiring | – |

---

## ⚡ Circuit Overview

### 1️⃣ For Addressable WS2812 LED Strip
```
Phone App → Bluetooth (HC-05) → Arduino → Data Pin → WS2812 LEDs → Power Supply (5V)
```
- **HC-05 TX → Arduino RX (Pin 10)**  
- **HC-05 RX → Arduino TX (Pin 11)** *(through voltage divider to 3.3V)*  
- **HC-05 VCC → 5V**  
- **HC-05 GND → GND**  
- **LED strip DIN → Arduino Pin 6**  
- **LED strip 5V & GND → external 5V supply (shared ground)**

### 2️⃣ For Analog RGB Strip
- Arduino PWM pins control **Red**, **Green**, and **Blue** channels through **MOSFETs**.

---

## 📱 Bluetooth Setup

1. Pair the **HC-05** module with your phone.  
   - Default name: `HC-05`  
   - Default PIN: `1234` or `0000`
2. Open a Bluetooth terminal app such as:
   - **Serial Bluetooth Terminal** (Android)
   - **Bluetooth Terminal HC-05**
3. Connect to the module and send text commands.

---

## 🧾 Command Protocol

| Command | Description |
|----------|--------------|
| `ON` | Turn all lights on |
| `OFF` | Turn all lights off |
| `RED` | Set solid red color |
| `GREEN` | Set solid green color |
| `BLUE` | Set solid blue color |
| `WHITE` | Set solid white color |
| `FLASH` | Flashing pattern |
| `FADE` | Fading color cycle |
| `RAINBOW` | Rainbow animation |

---

## 📶 Bluetooth Range
- Typical indoor range: **~10–15 meters**  
- Line-of-sight range: **up to 30 meters**
- Factors affecting range: walls, interference, antenna placement.

---

## 🔋 Power and Runtime
- **LEDs can stay on indefinitely** with a proper power supply.
- LED lifespan: ~50,000 hours typical.  
- For battery operation, expect **30–90 minutes** depending on brightness and number of LEDs.

---

## 🔐 Safety Notes
- Never drive AC mains lights directly from Arduino pins.  
- Use properly rated relays or MOSFETs for current loads.  
- Share **common ground** between Arduino, HC-05, and LED power.  
- Add a **1000 µF capacitor** across LED strip power input to prevent spikes.

---

## 🚀 Future Improvements
- Build a custom mobile app UI (buttons, sliders for brightness/patterns).  
- Add EEPROM storage for saved settings.  
- Integrate an RTC (real-time clock) for scheduling.  
- Add a microphone for sound-reactive effects.  
- Upgrade to **ESP32** for BLE + Wi-Fi control.
