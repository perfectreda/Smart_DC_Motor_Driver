<div align="center">

# ⚡ Smart DC Motor Driver PCB

**A compact, MCU-controlled DC motor driver for 12V systems**

![PCB](https://img.shields.io/badge/PCB-2--Layer-blue?style=for-the-badge&logo=kicad)
![Voltage](https://img.shields.io/badge/Voltage-12V_DC-orange?style=for-the-badge)
![Current](https://img.shields.io/badge/Current-Up_to_10A-red?style=for-the-badge)
![MCU](https://img.shields.io/badge/MCU-ESP32_%2F_STM32-green?style=for-the-badge&logo=espressif)
![License](https://img.shields.io/badge/License-Educational-lightgrey?style=for-the-badge)

*Built as a learning & portfolio project focused on real-world power electronics, PWM control, and high-current PCB design.*

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Electrical Specifications](#electrical-specifications)
- [System Architecture](#system-architecture)
- [Core Components](#core-components)
- [PCB Design Highlights](#pcb-design-highlights)
- [Safety & Design Considerations](#safety--design-considerations)
- [Getting Started](#getting-started)
- [Limitations (v1)](#limitations-v1)
- [Future Improvements](#future-improvements)
- [What This Project Demonstrates](#what-this-project-demonstrates)
- [License](#license)

---

## 🔍 Overview

This board moves beyond basic switching and targets **proper motor control behavior** with:
- Protection and current sensing
- Noise-aware layout practices
- PWM-based speed regulation via an external MCU (ESP32 / STM32 compatible)

It is designed as a practical introduction to **H-bridge motor control**, **high-current PCB layout**, and **inductive load protection** — all in a compact 12V form factor.

---

## ✨ Key Features

| Feature | Details |
|---|---|
| 🔋 Power Supply | 12V DC input |
| 🎛️ Speed Control | PWM via MCU (1–25 kHz range) |
| 🔄 Direction Control | H-bridge topology |
| 📊 Current Sensing | Load monitoring via shunt or Hall sensor |
| 🛡️ Reverse Polarity Protection | MOSFET-based input protection |
| ⚡ Flyback Protection | Inductive load spike suppression |
| 💡 Status LEDs | Power + fault indication |
| 🔌 UART Debug Interface | Serial telemetry output |
| 🔩 Screw Terminal Output | High-current rated motor connectors |

---

## 📐 Electrical Specifications

| Parameter | Value |
|---|---|
| Input Voltage | **12V DC** |
| Logic Voltage | **3.3V / 5V** (MCU compatible) |
| Max Motor Current | **~5–10A** (depends on MOSFET + copper width) |
| Switching Frequency | **1–25 kHz** (MCU PWM configured) |
| MOSFET Vds Margin | ≥ 30V recommended |

---

## 🏗️ System Architecture

The design is split into clean, isolated functional blocks:

```
┌─────────────────────────────────────────────────────────┐
│                     12V DC INPUT                        │
│            ┌──────────────────────┐                     │
│            │  Power Input Stage   │                     │
│            │  - Reverse polarity  │                     │
│            │  - Input filtering   │                     │
│            └──────────┬───────────┘                     │
│                       │                                 │
│            ┌──────────▼───────────┐                     │
│            │   Gate Drive Stage   │◄──── MCU PWM/DIR    │
│            │  - H-bridge MOSFETs  │                     │
│            │  - Gate resistors    │                     │
│            │  - Flyback paths     │                     │
│            └──────────┬───────────┘                     │
│                       │                                 │
│            ┌──────────▼───────────┐                     │
│            │  Motor Output Stage  │──── MOTOR           │
│            │  - Screw terminals   │                     │
│            │  - Wide copper pour  │                     │
│            └──────────┬───────────┘                     │
│                       │                                 │
│            ┌──────────▼───────────┐                     │
│            │   Sensing Stage      │──── MCU ADC         │
│            │  - Current sensing   │                     │
│            │  - Fault detection   │                     │
│            └──────────────────────┘                     │
└─────────────────────────────────────────────────────────┘
```

---

## 🔧 Core Components

| Component | Options |
|---|---|
| **N-MOSFETs** | IRLZ44N, AO series (logic-level preferred) |
| **Gate Resistors** | 10–33 Ω |
| **Pull-down Resistors** | 10 kΩ |
| **Current Sensor** | INA219 or shunt resistor setup |
| **MCU** | ESP32 or STM32 |
| **Protection Diodes** | Fast recovery / Schottky |
| **Connectors** | High-current rated screw terminal blocks |

---

## 🖥️ PCB Design Highlights

This project is heavily focused on **real PCB engineering constraints**:

- 🔴 **High-current trace routing** — wide pours, minimal resistance paths
- ⚡ **Separate power and logic grounds** — star topology grounding
- 📉 **Minimized switching loop area** — reduces EMI and ringing
- 🌡️ **MOSFET thermal spreading** — copper area + thermal vias
- 🔋 **Decoupling capacitors** — placed strategically near MOSFETs and MCU supply pins
- 📡 **EMI discipline** — layout minimizes high-dV/dt loop areas
- ⚡ **Short gate drive paths** — reduces switching noise and parasitic inductance

---

## ⚠️ Safety & Design Considerations

> **Important:** This board is designed for 12V DC motor loads which are inductive in nature. Always account for the following:

- **Voltage spikes** — motor loads generate back-EMF; flyback protection is mandatory
- **MOSFET Vds margin** — use devices rated ≥ 30V for a 12V system
- **Thermal management** — MOSFETs dissipate power under load; copper spreading is critical
- **Current sensing** — required for overload detection and fault protection
- **Fuse** — always include a fuse or PTC on the 12V input rail

---

## 🚀 Getting Started

### 1. Power Up

Connect a **12V DC power supply** to the input screw terminal. Verify the power LED lights up.

### 2. Connect MCU

Wire your MCU (ESP32 / STM32) to the PWM and direction control pins:

```
MCU Pin     →   Board Header
---------       ------------
GPIO (PWM)  →   PWM_IN
GPIO (DIR)  →   DIR_IN
GND         →   GND
3.3V / 5V   →   VCC_LOGIC
```

### 3. Attach Motor

Connect your DC motor to the output screw terminals.

### 4. Configure Firmware

Set your PWM frequency in firmware (recommended: **10–20 kHz** for most DC motors):

```c
// Example: ESP32 PWM setup (Arduino framework)
const int PWM_PIN    = 18;
const int DIR_PIN    = 19;
const int PWM_FREQ   = 20000;  // 20 kHz
const int PWM_CHANNEL = 0;
const int PWM_RES    = 8;      // 8-bit (0–255 duty cycle)

void setup() {
    ledcSetup(PWM_CHANNEL, PWM_FREQ, PWM_RES);
    ledcAttachPin(PWM_PIN, PWM_CHANNEL);
    pinMode(DIR_PIN, OUTPUT);
}

void loop() {
    digitalWrite(DIR_PIN, HIGH);       // Set direction
    ledcWrite(PWM_CHANNEL, 180);       // ~70% duty cycle
    delay(2000);

    ledcWrite(PWM_CHANNEL, 0);         // Stop
    delay(500);
}
```

### 5. Monitor Current (Optional)

Read the current sensing output via ADC or I²C (INA219) for load monitoring and fault detection.

---

## 🚧 Limitations (v1)

| Limitation | Notes |
|---|---|
| No isolated gate driver | Direct MCU-driven MOSFETs (low-side switching only) |
| Open-loop PWM only | No closed-loop speed feedback |
| Basic protection | No hardware overcurrent shutdown |
| No EMI certification | Not suitable for regulated/commercial products as-is |

---

## 🔮 Future Improvements

- [ ] **Dedicated gate driver IC** (e.g. IR2104, DRV8833, DRV8302)
- [ ] **Closed-loop speed control** (PID with encoder feedback)
- [ ] **Hardware overcurrent shutdown** (comparator + latch)
- [ ] **Better EMI filtering** (common-mode choke, TVS clamps)
- [ ] **4-layer PCB** (dedicated power plane + ground plane)
- [ ] **Industrial communication** (CAN / RS485)
- [ ] **Thermal protection** (NTC thermistor + MCU-controlled shutdown)

---

## 📚 What This Project Demonstrates

```
✅ DC motor control fundamentals
✅ H-bridge topology and operation
✅ PWM-based speed regulation
✅ Inductive load protection strategies
✅ High-current PCB layout techniques
✅ Practical embedded hardware integration
✅ Real-world power electronics design constraints
```

---

## 📜 License

**Open for educational and portfolio use.**
Commercial use requires full redesign validation and is not covered under this release.

---

<div align="center">

*If you found this useful, feel free to ⭐ star the repo!*

**Next milestone → Industrial driver version: gate driver IC + current control + thermal protection**

</div>
