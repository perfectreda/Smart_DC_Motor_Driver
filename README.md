# Smart DC Motor Driver Board V1

<p align="center">
  <img src="docs/images/3d_render_front.png" width="750" alt="3D Render Front">
</p>

<p align="center"># Smart DC Motor Driver Board V1

<p align="center">
  <img src="docs/images/3d_render_front.png" width="700">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ESP32-WROOM--32-blue">
  <img src="https://img.shields.io/badge/TB6612FNG-Motor%20Driver-green">
  <img src="https://img.shields.io/badge/INA219-Current%20Sensor-orange">
  <img src="https://img.shields.io/badge/PCB-4%20Layers-red">
  <img src="https://img.shields.io/badge/KiCad-10.0.1-success">
</p>

<p align="center">
  Wireless Motor Control • Current Monitoring • Protection Circuitry • Embedded Systems
</p>

---

## 📸 Project Gallery

<table>
<tr>
<td align="center">
<img src="docs/images/pcb_top.png" width="400"><br>
<b>PCB Top View</b>
</td>
<td align="center">
<img src="docs/images/pcb_bottom.png" width="400"><br>
<b>PCB Bottom View</b>
</td>
</tr>

<tr>
<td align="center">
<img src="docs/images/3d_render_front.png" width="400"><br>
<b>3D Front Render</b>
</td>
<td align="center">
<img src="docs/images/3d_render_back.png" width="400"><br>
<b>3D Back Render</b>
</td>
</tr>
</table>

---

# 📖 Overview

Smart DC Motor Driver Board V1 is a custom-designed 4-layer PCB developed around the ESP32 ecosystem for intelligent DC motor control applications.

The board integrates:

- ESP32-WROOM-32 microcontroller
- TB6612FNG H-Bridge motor driver
- INA219 current monitor
- LM2596 power regulation
- Input protection circuitry
- Temperature monitoring

---

# 🏗 System Architecture

<p align="center">
<img src="docs/images/block_diagram.png" width="800">
</p>

---

# ✨ Features

<table>
<tr>
<td width="50%">

### Control
- ESP32-WROOM-32
- WiFi
- Bluetooth
- UART Programming

### Motor Driver
- TB6612FNG
- PWM Speed Control
- Direction Control
- Standby Mode

</td>

<td width="50%">

### Monitoring
- INA219 Current Sensor
- Voltage Measurement
- Power Monitoring
- NTC Temperature Sensor

### Protection
- TVS Diode
- Resettable Fuse
- MOSFET Power Switch
- Ground Plane Design

</td>
</tr>
</table>

---

# ⚙ Hardware Specifications

| Parameter | Value |
|------------|---------|
| Input Voltage | 12V DC |
| Logic Voltage | 3.3V |
| MCU | ESP32-WROOM-32 |
| Motor Driver | TB6612FNG |
| Current Sensor | INA219 |
| PCB Layers | 4 |
| PCB Size | 96.28 × 72.90 mm |
| Thickness | 1.6 mm |
| Material | FR4 |
| EDA Tool | KiCad 10.0.1 |

---

# 🔌 ESP32 Pin Mapping

| GPIO | Function |
|--------|------------|
| GPIO21 | SDA |
| GPIO22 | SCL |
| GPIO25 | PWMA |
| GPIO27 | AIN1 |
| GPIO14 | AIN2 |
| GPIO33 | STBY |
| GPIO34 | NTC ADC |
| GPIO15 | Fault LED |
| TXD0 | UART TX |
| RXD0 | UART RX |
| GPIO0 | Boot Mode |

---

# 📂 Repository Structure

```text
Smart_DC_Motor_Driver/
│
├── Hardware/
│   ├── BOM/
│   ├── Gerbers/
│   ├── Drill Files/
│   └── Reports/
│
├── docs/
│   └── images/
│       ├── pcb_top.png
│       ├── pcb_bottom.png
│       ├── 3d_render_front.png
│       ├── 3d_render_back.png
│       ├── schematic.png
│       └── block_diagram.png
│
└── README.md
```

---

# 🛠 Manufacturing

<details>
<summary><b>Click to expand manufacturing information</b></summary>

### PCB Specifications

| Parameter | Value |
|------------|---------|
| Layers | 4 |
| Thickness | 1.6 mm |
| Copper Weight | 1 oz |
| Surface Finish | ENIG / HASL |
| Material | FR4 |

Upload all files inside:

```text
Hardware/Gerbers/
```

to your PCB manufacturer.

</details>

---

# 🚀 Programming

### UART Header

| Pin | Signal |
|------|---------|
| 1 | 3.3V |
| 2 | GND |
| 3 | TX |
| 4 | RX |
| 5 | GPIO0 |
| 6 | EN |

### Flashing

```bash
esptool.py write_flash firmware.bin
```

Compatible with:

- Arduino IDE
- PlatformIO
- ESP-IDF

---

# 📊 PCB Statistics

| Item | Count |
|---------|---------|
| PCB Layers | 4 |
| Components | 40+ |
| Vias | 47 |
| Mounting Holes | 4 |
| Current Sensor | 1 |
| Motor Driver Channels | 2 |

---

# 👨‍💻 Author

### Redha

Electrical Engineering Student

**Specialization:** Energy Conversion & Embedded Systems

GitHub:

https://github.com/perfectreda

---

# 📜 License

Released under the MIT License.
See `LICENSE` for details.6612FNG">
  <img src="https://img.shields.io/badge/INA219-Current%20Sensor-orange?style=for-the-badge" alt="INA219">
  <img src="https://img.shields.io/badge/PCB-2%20Layers-red?style=for-the-badge" alt="2 Layers">
  <img src="https://img.shields.io/badge/KiCad-10.0.1-success?style=for-the-badge" alt="KiCad">
</p>

<p align="center">
  <b>Wireless DC Motor Control • Real-Time Current Monitoring • Embedded Hardware Design</b>
</p>

---

## 📌 Overview

The **Smart DC Motor Driver Board V1** is a compact **2-layer PCB** designed for intelligent DC motor control using the **ESP32-WROOM-32**, **TB6612FNG**, and **INA219**.

It combines:
- wireless control through ESP32
- dual motor driving
- real-time current sensing
- input protection
- temperature monitoring
- UART flashing support

---

## 🖼 Project Gallery

<table>
  <tr>
    <td align="center">
      <img src="docs/images/pcb_top.png" width="380" alt="PCB Top View"><br>
      <b>PCB Top View</b>
    </td>
    <td align="center">
      <img src="docs/images/pcb_bottom.png" width="380" alt="PCB Bottom View"><br>
      <b>PCB Bottom View</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="docs/images/3d_render_front.png" width="380" alt="3D Front Render"><br>
      <b>3D Front Render</b>
    </td>
    <td align="center">
      <img src="docs/images/3d_render_back.png" width="380" alt="3D Back Render"><br>
      <b>3D Back Render</b>
    </td>
  </tr>
</table>

---

## 🧠 System Architecture

<p align="center">
  <img src="docs/images/block_diagram.png" width="850" alt="Block Diagram">
</p>

```text
+12V Input
    │
    ├── Protection Stage
    │   ├── Resettable Fuse
    │   ├── TVS Diode
    │   └── P-MOSFET Power Switch
    │
    ├── LM2596 Buck Converter
    │   └── 12V → 3.3V Logic Supply
    │
    └── Motor + Logic Control
        ├── ESP32-WROOM-32
        ├── TB6612FNG Motor Driver
        ├── INA219 Current Sensor
        └── NTC Temperature Sensor
