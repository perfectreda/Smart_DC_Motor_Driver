# Smart DC Motor Driver Board V1

A compact 4-layer PCB for smart DC motor control, built around the **ESP32-WROOM-32**, **TB6612FNG** dual motor driver, and **INA219** current sensor. Designed for embedded/IoT applications requiring wireless motor control with real-time current monitoring.

---

## Features

- **ESP32-WROOM-32** — WiFi + Bluetooth, full GPIO control
- **TB6612FNG** — dual H-bridge DC motor driver (continuous 1.2A, peak 3.2A per channel)
- **INA219** — I²C current/voltage sensor for real-time motor current monitoring
- **LM2596 Buck Module** — onboard 12V → 3.3V regulation for logic supply
- **IRF4905 P-MOSFET** — controlled power switch on the 12V rail
- **PTVS12VZ1USK TVS Diode** — transient voltage spike protection
- **MF-R500 Resettable Fuse** — overcurrent protection on the input
- **NTC Thermistor** — temperature monitoring
- **3 Status LEDs** — POWER / MOTOR / FAULT indicators
- **UART Programming Header (J2)** — TX, RX, IO0, EN pins for flashing
- **Screw Terminal Connectors** — motor and power connections

---

## Specifications

| Parameter | Value |
|---|---|
| Input Voltage | 12V DC |
| Logic Voltage | 3.3V (onboard regulated) |
| Board Size | 96.28 × 72.90 mm |
| Layer Count | 4 (Front, In1.Cu, In2.Cu, Back) |
| PCB Thickness | 1.6 mm |
| Material | FR4 |
| Min Track Width | 0.2 mm |
| Min Clearance | 0.15 mm |
| EDA Tool | KiCad 10.0.1 |

---

## Bill of Materials

| Reference | Qty | Value / Part | Package |
|---|---|---|---|
| U1 | 1 | LM2596 Buck Module | Module board |
| U2 | 1 | ESP32-WROOM-32 | RF Module |
| U3 | 1 | TB6612FNG | SSOP-24 |
| U4 | 1 | INA219AxD | SOIC-8 |
| Q1 | 1 | IRF4905 P-MOSFET | TO-220-3 |
| D1 | 1 | PTVS12VZ1USK TVS Diode | Nexperia DSN1608 |
| D2 | 1 | POWER LED | LED 0805 |
| D3 | 1 | MOTOR LED | LED 0805 |
| D4 | 1 | FAULT LED | LED 0805 |
| F1 | 1 | MF-R500 Resettable Fuse | Fuse 1206 |
| TH1 | 1 | NTC Thermistor | 0805 |
| SW1 | 1 | Tactile Push Button (EN) | SPST TL3342 |
| J1, J3 | 2 | Screw Terminal 2-pin | Phoenix MKDS 5.08mm |
| J2 | 1 | Pin Header 6-pin (UART) | 2.54mm vertical |
| C1 | 1 | 100µF | — |
| C4, C6, C10, C11 | 4 | 100µF | CP Elec 8×10mm |
| C2, C3, C5, C7, C8, C9, C12 | 7 | 100nF | C 0805 |
| R1, R3, R4, R11 | 4 | 10kΩ | R 0805 |
| R2 | 1 | 100kΩ | R 0805 |
| R5, R6, R7 | 3 | 330Ω | R 0805 |
| R8, R9 | 2 | 4.7kΩ | R 0805 |
| R10 | 1 | 0.1Ω (shunt) | R 0805 |

---

## Pin Mapping (ESP32 → Peripherals)

| ESP32 GPIO | Signal | Connected To |
|---|---|---|
| IO21 | SDA | INA219 I²C |
| IO22 | SCL | INA219 I²C |
| IO25 | PWMA | TB6612FNG PWM |
| IO27 | AIN1 | TB6612FNG direction |
| IO14 | AIN2 | TB6612FNG direction |
| IO33 | STBY | TB6612FNG standby |
| IO23 (via EN) | EN | MOSFET gate (power switch) |
| IO32 | GPIO32 | LED / indicator |
| IO15 | GPIO15 | General purpose |
| IO34 | NTC | Thermistor ADC |
| TXD0 | TX | UART header (J2) |
| RXD0 | RX | UART header (J2) |
| IO0 | IO0 | Boot mode / UART header |
| EN | EN | Reset / UART header |

---

## PCB Layer Stack

```
[Top Silk]
[Top Paste]
[Top Mask]
 L1 — Front Copper        (signal + power)
      FR4 0.48mm
 L2 — In1.Cu              (internal signal)
      FR4 0.48mm
 L3 — In2.Cu              (internal signal)
      FR4 0.48mm
 L4 — Back Copper         (GND plane)
[Bottom Mask]
[Bottom Paste]
[Bottom Silk]
```

---

## Drill Summary

| Type | Size | Count |
|---|---|---|
| PTH via | 0.3mm | 47 |
| PTH component | 0.2mm | 12 |
| PTH component | 1.0mm | 6 |
| PTH component | 1.1mm | 3 |
| PTH component | 1.2mm | 4 |
| PTH component | 1.3mm | 4 |
| NPTH mounting hole | 3.2mm | 4 |

---

## Repository Structure

```
├── Hardware/
│   ├── BOM/
│   │   └── Smart Power Management Board.csv
│   ├── Gerbers/
│   │   ├── SMART_DC_MOTOR_DRIVER-Front.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-Back.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-In1_Cu.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-In2_Cu.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-F_Mask.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-B_Mask.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-F_Paste.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-B_Paste.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-F_Silkscreen.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-B_Silkscreen.gbr
│   │   ├── SMART_DC_MOTOR_DRIVER-Edge_Cuts.gbr
│   │   └── SMART_DC_MOTOR_DRIVER-job.gbrjob
│   ├── Drill files/
│   │   ├── SMART_DC_MOTOR_DRIVER-PTH.drl
│   │   └── SMART_DC_MOTOR_DRIVER-NPTH.drl
│   └── Report File/
│       └── SMART_DC_MOTOR_DRIVER-drl.rpt
└── README.md
```

---

## Getting Started

### Programming the ESP32

Connect a USB-to-Serial adapter to **J2**:

| J2 Pin | Signal | Adapter |
|---|---|---|
| 1 | 3.3V | 3.3V |
| 2 | GND | GND |
| 3 | TX | RX |
| 4 | RX | TX |
| 5 | IO0 | Pull LOW to enter flash mode |
| 6 | EN | Pull LOW then HIGH to reset |

Flash using Arduino IDE or `esptool.py`.

### Manufacturing

Send the contents of `Hardware/Gerbers/` to your PCB manufacturer. The `.gbrjob` file contains the full stackup definition. Specify **4-layer, 1.6mm FR4, HASL or ENIG finish**.

---

## Schematic Signals Reference

| Net Name | Description |
|---|---|
| `+12V_FUSED` | Input after fuse F1 |
| `12V_PROTECTED` | Output after MOSFET Q1 |
| `3.3V` | Regulated logic supply |
| `GND` | Common ground |
| `SDA / SCL` | I²C bus to INA219 |
| `PWMA` | Motor PWM from ESP32 |
| `AIN1 / AIN2` | Motor direction control |
| `STBY` | TB6612 standby control |
| `NTC` | Thermistor ADC input |

---

## Author

**Redha** — [@perfectreda](https://github.com/perfectreda)

Electrical Engineering student — Specialization: Energy Conversion & Embedded Systems.

---

## License

Hardware design files are open-source. See [LICENSE](LICENSE) for details.
