# Schrödinger Watch

## Overview
Schrödinger Watch is an open-source PCB watch project powered by an ESP32-S3-WROOM module. The project is designed for DIY enthusiasts and embedded system developers who want to explore low-power wearable technology. The watch features an RTC, an OLED display, multiple push buttons, battery monitoring, and alarm functionalities.

## Features
- **ESP32-S3-WROOM (40-pin)** for processing and connectivity
- **RTC DS3231** with alarm functionality
- **I2C OLED display** for time and notifications
- **3.7V Li-Po battery** with **TP4056 charging module**
- **Push buttons, LEDs, buzzer** for user interaction
- **Micro-USB port** for charging and communication
- **Voltage divider for battery status detection**
- **P-MOSFET for automatic power switching**
- **Schottky diode for USB protection**

## Getting Started
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/schrodinger-watch.git
   ```
2. Install dependencies (Arduino libraries, ESP32 board package, etc.).
3. Compile and upload firmware using Arduino IDE or PlatformIO.
4. Assemble the hardware components following the PCB layout.
5. Power up the watch and test its functionality.

## Contribution Guidelines
We welcome contributions from the community! Here’s how you can contribute:

### Reporting Issues
- If you find a bug or have suggestions for improvements, open an issue [here](https://github.com/your-repo/schrodinger-watch/issues).
- Provide clear steps to reproduce bugs and expected behavior.

### Submitting Pull Requests
1. Fork the repository.
2. Create a new branch for your feature/fix.
   ```sh
   git checkout -b feature-new-functionality
   ```
3. Commit changes with a meaningful message.
   ```sh
   git commit -m "Added new alarm functionality"
   ```
4. Push to your fork and submit a Pull Request.
   ```sh
   git push origin feature-new-functionality
   ```
5. Wait for review and feedback before merging.

### Coding Standards
- Follow clean and structured coding practices.
- Document your code with comments where necessary.
- Ensure compatibility with ESP32-S3 and avoid breaking existing features.

### Documentation Contributions
- Improve project documentation by updating README, wiki, or adding examples.
- Provide clear instructions for assembling and programming the watch.

## License
This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## Support & Community
- Join discussions and share your ideas in our community forums.
- Follow project updates on [GitHub](https://github.com/your-repo/schrodinger-watch).
- For any queries, contact us via issues or email.

Happy hacking! 🚀

