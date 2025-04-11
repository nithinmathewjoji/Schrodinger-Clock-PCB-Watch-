# Schrödinger Watch - Open Source Smartwatch

![Image](https://github.com/user-attachments/assets/ff7e76a2-2ea0-487d-b156-6dcd2752788e)
*A compact, open-source smartwatch powered by the ESP32-S3-WROOM with real-time clock, battery monitoring, and USB charging.*

---

## 📑 Index

1. [Introduction](#introduction)
2. [Features](#features)
3. [Hardware Overview](#hardware-overview)
4. [Schematic & PCB Design](#schematic--pcb-design)
5. [Bill of Materials (BoM)](#bill-of-materials-bom)
6. [Firmware & Software](#firmware--software)
7. [Assembly & Soldering Guide](#assembly--soldering-guide)
8. [Usage Guide](#usage-guide)
9. [Power Management](#power-management)
10. [Downloads](#downloads)
11. [Firmware](#firmware)
12. [Visit Interactive BOM](https://nithinmathewjoji.github.io/Schrodinger-Clock-PCB-Watch-/)
13. [Contributing](#contributing)
14. [License](#license)
15. [Acknowledgments](#acknowledgments)

---

## Introduction

The **Schrödinger Watch** is an ESP32-S3-based open-source smartwatch designed with a focus on **compact PCB layout**, **low power consumption**, and **modular features**. It integrates **RTC, I2C display, battery monitoring**, and a **USB charging circuit**, making it a versatile platform for wearable tech enthusiasts.

---

## Features

| Feature                  | Description |
|--------------------------|-------------|
| **Microcontroller**      | ESP32-S3-WROOM (40-pin) |
| **Display**              | I2C OLED |
| **RTC Module**          | DS3231 (with alarm) |
| **Buttons**              | 3 push buttons (pull-up) |
| **Buzzer**               | Included for alarms and notifications |
| **Battery**              | 3.7V Li-Po battery |
| **Charging Circuit**     | TP4056 for Li-Po charging |
| **Battery Monitoring**   | Voltage divider for ADC measurement |
| **USB Communication**    | CP2102 USB programmer |
| **Power Switching**      | *P-MOSFET for auto power control |
| **Protection Circuit**   | Schottky diode for USB protection |

* *feature will be added on the next revision
---

## Hardware Overview

The smartwatch is designed with **SMD components** for compactness. Below is the pin mapping:

| Component   | ESP32 GPIO | Function |
|------------|------------|----------|
| OLED SDA   | GPIO 20   | I2C SDA  |
| OLED SCL   | GPIO 21   | I2C SCL  |
| RTC SDA   | GPIO 20   | I2C SDA  |
| RTC SCL   | GPIO 21   | I2C SCL  |
| RTC Alarm  | GPIO 11 | SQW/INT to ESP32 |
| Battery ADC | GPIO7 | Voltage divider to ESP32 Analog Pin |
| LED        | GPIO 2    | Status Indication |
| LED        | GPIO 3    | Status Indication |
| LED        | GPIO 4    | Status Indication |
| Push Button 1 | GPIO 20  | User Input |
| Push Button 2 | GPIO 21 | User Input |
| Push Button 3 | GPIO 22  | User Input |

* refer circuit  [Schrödinger_Watch_schematics](https://github.com/nithinmathewjoji/Schrodinger-Clock-PCB-Watch-/blob/master/Schematics/schematic.pdf) for more detailed pin out.and pin assignments

---

## Schematic & PCB Design

The Schrödinger Watch PCB was designed using **KiCad**. The schematic consists of:
- ESP32-S3-WROOM microcontroller
- RTC DS3231 with backup battery support
- Power management with TP4056 and P-MOSFET
- I2C OLED display
- Battery voltage detection circuit
- USB programmer (CP2102)

![Image](https://github.com/user-attachments/assets/05f76e5b-197c-40fe-948d-525a1f453791)

**PCB Highlights:**
- **2-layer compact design**
- **Optimized power trace routing**
- **Thermal relief for heat dissipation**
- **Dedicated test points for debugging**


---

##  Bill of Materials (BoM)

| Component | Quantity | Specification |
|-----------|----------|--------------|
| ESP32-S3-WROOM | 1 | 40-pin module |
| OLED Display | 1 | I2C, 128x64 |
| DS3231 RTC | 1 | Real-time clock module |
| Li-Po Battery | 1 | 3.7V, 500mAh |
| TP4056 Module | 1 | Battery charger |
| CP2102 | 1 | USB-to-serial |
| Buzzer | 1 | 3V piezo |
| Push Buttons | 3 | Momentary switch |
| Resistors & Capacitors | Various | SMD components |

---

##  Firmware & Software

The firmware is written in **Arduino** using the ESP32 library. It supports:
- RTC time synchronization
- OLED display updates
- Battery monitoring
- Button interactions
- Alarm system with buzzer



---

##  Assembly & Soldering Guide

### Tools Required:
- Soldering iron with fine tip
- SMD soldering paste
- Hot air reflow station (optional)
- Multimeter for testing

### Assembly Steps:
1. Solder the **ESP32-S3-WROOM** module first.
2. Attach **RTC DS3231** and connect alarm pin to ESP32.
3. Solder **resistors, capacitors, and power circuits**.
4. Mount **OLED display** and ensure I2C connectivity.
5. Connect **battery and charging module**.
6. Flash firmware and test.

---

##  Usage Guide

### Powering On:
Press and hold the power button. The watch will display the **time, battery status**, and active alarms.

### Setting Time:
Use the **serial monitor** to set the time in RTC using `setTime()`.

### Battery Monitoring:
Battery percentage is displayed on-screen and can be accessed through the serial monitor.

### Alarm Function:
The RTC alarm triggers a buzzer sound at the set time.

---

##  Power Management

- **Automatic Power Switching:** P-MOSFET allows seamless switching between USB and battery.
- **USB Protection:** Schottky diode prevents reverse current flow.
- **Low Power Mode:** ESP32 enters deep sleep when inactive to conserve power.

---

## Downloads
-  **Download KiCad files:** [Schrödinger_Watch.kicad_pcb](https://github.com/nithinmathewjoji/Schrodinger-Clock-PCB-Watch-/tree/master/KiCAD-Files)
-  **Download Code:** [Schrödinger_Watch.ino](path_to_file)
-  **Schematics:** [Schrödinger_Watch_schematics](https://github.com/nithinmathewjoji/Schrodinger-Clock-PCB-Watch-/blob/master/Schematics/schematic.pdf)

---

## Firmware

- **Schrödinger Watch Firmware:** [firmware_not_yet_released_please_hold_on]()

##  Contributing

We welcome contributions! If you’d like to improve the watch, please:
1. Fork the repository.
2. Create a new branch.
3. Submit a Pull Request with details.

---

##  License

This project is licensed under the **MIT License**. Feel free to use, modify, and distribute it with proper attribution.

---

## Acknowledgments

Special thanks to the **open-source hardware community** for inspiring this project! 🚀
