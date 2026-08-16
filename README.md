# 🛰️ Dual-LoRa High-Altitude GNSS Tracking System (IREC 2025)

An avionic-grade, dual-band telemetry and GNSS tracking board developed for high-altitude sounding rockets and aerospace payload challenges (IREC 2025).

---

<p align="center">
  <img src="Tracker%20IREC.png" alt="IREC Tracker PCB Preview" width="750">
</p>

---

## 📌 Project Overview

This tracking system provides real-time recovery telemetry, multi-constellation positional coordinates, barometric altitude, and full power diagnostics over redundant long-range RF links during sounding rocket flights.

---

## 🛠️ Hardware Architecture & Specifications

### 1. MicroController Unit (MCU)
* **STM32F446RET6:** 32-bit ARM Cortex-M4 @ 180 MHz with DSP and FPU.
* **Interfaces:** On-board SWD programming/debugging interface, external crystal oscillators (HSE/LSE), and hardware reset circuitry.

### 2. Dual-Band RF & Long-Range Telemetry
* **LoRa Module 1:** Ebyte **E22-900M33S** (SPI Interface, 868/915 MHz, +33 dBm / 2W output power).
* **LoRa Module 2:** Ebyte **E22-400T37S** (UART Interface, 433/470 MHz, +37 dBm / 5W ultra high-power telemetry link).
* **RF Output:** Independent 50-ohm matched external antenna connectors for dual-frequency operations.

### 3. Navigation & Environmental Sensors
* **GNSS Receiver:** Quectel **L86 GPS** (Integrated patch antenna with support for external active antennas, PPS pulse output, and battery backup support).
* **Barometer / Altimeter:** Bosch Sensortec **BME280** (High-precision I2C digital pressure, altitude, and temperature sensor).

### 4. Data Logging & External Interfaces
* **NOR Flash Memory:** **W25Q256JV** (256 Mbit / 32 MB High-Speed Quad-SPI / SPI Flash for flight data recording).
* **MicroSD Card Storage:** Onboard SPI-driven MicroSD socket with card detect for high-capacity telemetry logging.
* **USB-to-UART Bridge:** FTDI **FT232RNL** via Mini-USB for direct serial debugging and live telemetry readouts.
* **Auxiliary Headers:** Dedicated GPIO and I2C expansion pin headers.

### 5. Power Management & Hardware Diagnostics
* **Step-Down Switching Regulator:** **AP63205** (5V / 2A high-efficiency synchronous buck converter).
* **Linear Low-Dropout Regulator:** **AMS1117-3.3** (Clean 3.3V power rail for MCU, sensors, and peripherals; High PSRR).
* **Current & Voltage Sensing:** High-side current sensing via **INA139NA** current shunt monitor paired with a precision resistor divider for continuous battery diagnostics.
* **RTC & Backup Power:** Dedicated external battery line (`V_BCKP`) for GPS ephemeris retention and hot-start support.
* **Status Indicators:** Transistor-driven audible buzzer along with multi-color diagnostic LEDs for system, GPS fix, and telemetry status.

---

## 📁 Repository Structure

```text
├── Altium PROJECT/          # Altium Designer project files (.PrjPcb, .PcbDoc)
├── Altium SCHEMATIC/        # Modular schematic sheets (.SchDoc)
├── GPS_TRACKER_IREC.pdf     # Complete schematic and hardware export
├── Tracker IREC.png         # Hardware render / preview image
└── README.md                # Project documentation and specifications
