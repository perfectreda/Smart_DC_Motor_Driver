# Smart DC Motor Driver Board V1

<p align="center">
  <img src="docs/images/3d_render_front.png" width="750" alt="3D Render Front">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ESP32-WROOM--32-blue?style=for-the-badge" alt="ESP32">
  <img src="https://img.shields.io/badge/TB6612FNG-Motor%20Driver-green?style=for-the-badge" alt="TB6612FNG">
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
