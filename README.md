# Schrödinger Clock - Open Source Smartwatch (Prototype⚠️)

<p align="center">Sponsored By </p>
<p align="center">
  <a href="https://pcbway.com/g/D6Z94Y">
    <img src="./PCBWay logo.png" alt="PCBWay" width="200"/>
  </a>
</p>


![Image](https://github.com/user-attachments/assets/ff7e76a2-2ea0-487d-b156-6dcd2752788e)
*A compact, open-source smartwatch powered by the ESP32-S3-WROOM with real-time clock, battery monitoring, and USB charging.*

---

## 📑 Index

1. [Introduction](#introduction)
2. [Features](#features)
3. [Hardware Overview](#hardware-overview)
4. [Sponsorship and Support](#Sponsorship-and-Support)
5. [Schematic & PCB Design](#schematic--pcb-design)
6. [Known issues & Fix](#Known-issues-and-Fix)
7. [Bill of Materials (BoM)](#bill-of-materials-bom)
8. [Firmware & Software](#firmware--software)
9. [Assembly & Soldering Guide](#assembly--soldering-guide)
10. [Usage Guide](#usage-guide)
11. [Power Management](#power-management)
12. [Downloads](#downloads)
13. [Firmware](#firmware)
14. [Visit Interactive BOM](https://nithinmathewjoji.github.io/Schrodinger-Clock-PCB-Watch-/)
15. [Contributing](#contributing)
16. [License](#license)
17. [Acknowledgments](#acknowledgments)

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
| Push Button 1 | GPIO 12  | User Input |
| Push Button 2 | GPIO 13 | User Input |
| Push Button 3 | GPIO 22  | User Input |

* refer circuit  [Schrödinger_Watch_schematics](https://github.com/nithinmathewjoji/Schrodinger-Clock-PCB-Watch-/blob/master/Schematics/schematic.pdf) for more detailed pin out.and pin assignments

---

## Sponsorship and Support

<p align="center">
  <a href="https://pcbway.com/g/D6Z94Y">
    <img src="./PCBWay logo.png" alt="PCBWay" width="250"/>
  </a>
</p>

### 🙏 Thank You, PCBWay!

This project was proudly sponsored by [**PCBWay**](https://pcbway.com/g/D6Z94Y).  

Their support in fabricating the custom PCB for the Schrödinger Watch has been invaluable. The quality, precision, and delivery speed were exceptional — and I’m extremely grateful for their contribution to the maker and open-source community.

If you're looking for reliable PCB prototyping, assembly, or 3D printing services, I highly recommend [**PCBWay**](https://pcbway.com/g/D6Z94Y).


## Schematic & PCB Design

The Schrödinger Watch PCB was designed using **KiCad**. The schematic consists of:
- ESP32-S3-WROOM microcontroller
- RTC DS3231 with backup battery support
- Power management with TP4056 and P-MOSFET
- I2C OLED display
- Battery voltage detection circuit
- USB programmer (CP2102)

![Image](https://github.com/user-attachments/assets/e0cc1d44-5b90-4ff5-a8fc-488cb06ea098)

**PCB Highlights:**
- **2-layer compact design**
- **Optimized power trace routing**
- **Thermal relief for heat dissipation**
- **Dedicated test points for debugging**


---


## Known issues and Fix

Schrödinger Watch ⌚ – ESP32-S3 DIY Smartwatch

This is the **Schrödinger Watch**, a DIY smartwatch powered by the **ESP32-S3-WROOM**. It's a fully open-source hardware project, designed and assembled from scratch, with a focus on learning, hacking, and creativity.

> ⚠️ **Note:** This is **Rev 1** of the hardware. While functional, it contains some known hardware issues listed below. A refined **Rev 2** is under development and will be released by **September 2025** with additional features and improved reliability.

These are hardware issues identified after assembly and testing:

1. **Missing CE Connection on TP4056:**
   - ⚠️ The CE (Chip Enable) pin was left floating, causing the charging IC to remain disabled.
   - ✅ *Fix:* A patch wire has been added to tie CE to GND manually.

2. **AMS1117 3.3V LDO Lacks Input/Output Capacitors:**
   - ⚠️ Without these caps, voltage regulation is unstable (outputting ~2.4V instead of 3.3V).
   - ✅ *Fix:* Patch capacitors (10µF input, 22µF output) have been manually added close to the LDO pins.

3. **No Pull-Down Resistors for Pushbuttons:**
   - ⚠️ Causes GPIO pins to float, leading to erratic behavior.
   - ✅ *Fix:* External 10kΩ pull-down resistors were added to stabilize the inputs.

4.  **Soldering Considerations:**
   - The board is fully designed with **SMD components** for a compact layout.
   - All components were **hand-soldered** using a soldering iron, without hot air or reflow equipment. Minor imperfections exist, but the board is fully functional.

---

#  What's Coming in Rev 2 (ETA: September 2025)

Rev 2 will be a major update with all hardware issues addressed and new features, including:

- ✅ Proper power rail decoupling and CE management
- ✅ Integrated **MPU6050** IMU for motion sensing
- ✅ Improved button input system
- ✅ Compact routing 
- ✅ Better power management and battery indication
- ✅ Optional haptic feedback (planned)
- ✅ Additional user-customizable GPIOs

 📌 Disclaimer

This is a learning-oriented DIY project and should not be considered a finished consumer product. Use with care and contribute to make it better!




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

🛠️ Libraries Used

- [U8g2](https://github.com/olikraus/u8g2)
- [RTClib](https://github.com/adafruit/RTClib)

Install via Arduino Library Manager or PlatformIO.

🚧 Known Hardware Issues (Rev 1)

- ❌ No CE connection to TP4056 (manually patched)
- ❌ No input/output capacitors on MIC39100/AMS1117 LDO (caused unstable voltage)
- ❌ Button GPIOs conflicted with I2C (now reassigned to GPIOs 12–14)
- ❌ No pull-down resistors for switches (using `INPUT_PULLDOWN` in firmware)

# 💾 Firmware Code

```cpp
#include <Wire.h>
#include <U8g2lib.h>
#include <RTClib.h>

// I2C Pins
#define SDA_PIN 20
#define SCL_PIN 21

// GPIO Definitions
#define LED_PIN       2
#define BATTERY_ADC   7
#define RTC_ALARM_PIN 11

#define BUTTON1 12
#define BUTTON2 13
#define BUTTON3 14

U8G2_SSD1306_128X64_NONAME_F_HW_I2C u8g2(U8G2_R0, U8X8_PIN_NONE);
RTC_DS3231 rtc;

void setup() {
  Serial.begin(115200);

  Wire.begin(SDA_PIN, SCL_PIN);
  u8g2.begin();

  pinMode(LED_PIN, OUTPUT);
  pinMode(RTC_ALARM_PIN, INPUT);
  pinMode(BATTERY_ADC, INPUT);

  pinMode(BUTTON1, INPUT_PULLDOWN);
  pinMode(BUTTON2, INPUT_PULLDOWN);
  pinMode(BUTTON3, INPUT_PULLDOWN);

  if (!rtc.begin()) {
    u8g2.clearBuffer();
    u8g2.setFont(u8g2_font_ncenB08_tr);
    u8g2.drawStr(0, 20, "RTC Not Found");
    u8g2.sendBuffer();
    while (1);
  }

  if (rtc.lostPower()) {
    rtc.adjust(DateTime(F(__DATE__), F(__TIME__)));
  }

  u8g2.clearBuffer();
  u8g2.setFont(u8g2_font_6x10_tr);
  u8g2.drawStr(0, 10, "Schrodinger Watch");
  u8g2.sendBuffer();
  delay(1000);
}

void loop() {
  DateTime now = rtc.now();

  char timeStr[9];
  sprintf(timeStr, "%02d:%02d:%02d", now.hour(), now.minute(), now.second());

  float batteryVoltage = analogRead(BATTERY_ADC) * (3.3 / 4095.0) * 2;  // Adjust based on divider
  char voltStr[10];
  dtostrf(batteryVoltage, 4, 2, voltStr);

  u8g2.clearBuffer();
  u8g2.setFont(u8g2_font_logisoso38_tr);
  u8g2.drawStr(0, 50, timeStr);
  u8g2.setFont(u8g2_font_6x10_tr);
  u8g2.drawStr(0, 62, ("BAT: " + String(voltStr) + "V").c_str());
  u8g2.sendBuffer();

  digitalWrite(LED_PIN, !digitalRead(LED_PIN));  // Blink LED

  if (digitalRead(BUTTON1)) Serial.println("Button 1 Pressed");
  if (digitalRead(BUTTON2)) Serial.println("Button 2 Pressed");
  if (digitalRead(BUTTON3)) Serial.println("Button 3 Pressed");

  delay(1000);
}


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

Special thanks to the **open-source hardware community** for inspiring this project!
