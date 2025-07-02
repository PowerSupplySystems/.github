# ⚡ Power Supply System (PSS)

A smart, modular, and embedded **Power Supply System** designed for modern edge devices and IoT applications. PSS is a robust, intelligent power solution that can **monitor**, **regulate**, and **communicate** power states with the main processor, making it ideal for low-power systems, battery-operated devices, and embedded industrial applications.

---

## 🔧 Hardware Overview

The Power Supply System includes the following hardware features:

### ✅ Power Inputs and Outputs

* **Input Voltage:** 0–24V (DC) input with **eFuse** protection.
* **Outputs:**

  * 2x **Fixed** output rails: 5V, 3.3V
  * 2x **Adjustable** output rails (0.8V – 20V):

    * Manual control (via register)
    * Automatic control via **MCU/PLD algorithm**
  * **Dropout handling** for high-current stability.

### 🔋 Battery Management

* 2-Cell battery charger and manager
* Smart charge/discharge cycles
* Safety cutoff and protection features

### 🧠 Control Unit

* **MCU** as a co-processor to control power logic
* **Environment sensors** (temperature, possibly humidity)
* **Current/Voltage/Power sensing** on both input and output lines
* **Status Pins**: Configurable PWM mode pins for LED indicators
* **Interrupt/Event handling** for runtime power events

### 🛠 IO & Interfaces

* **Programmable IOs** (user-configurable)
* **Communication Interfaces:**

  * UART (with OTA support)
  * SPI
  * I2C

---

## 🔐 Firmware Features

The embedded firmware on the co-processor enables full automation, protection, and secure communication:

* **Encrypted Firmware Support**
* **UART-based OTA (Over-The-Air) update**
* **Modbus protocol** support for communication
* Built-in **event-driven firmware logic**
* Safety algorithms (e.g., over-temp cutoff, overcurrent, fallback mode)

---

## 📡 PSS\_API: Host Interface Library

PSS\_API provides a high-level interface for the main processor to control and query the Power Supply System.

### ✨ Features:

* Written in **C**
* Modular and lightweight
* High-level abstraction to interact with PSS (e.g., set voltage, read power usage)
* **CMake-based** build system
* Supports **multi-target MCUs**

  * STM32, ESP32, NXP, RP2040 (planned)
* Examples and demo applications

---

## 💡 Possible Enhancements and Ideas

Here are some additional ideas to make the PSS module even more powerful:

### Hardware Ideas

* Add **RTC + Supercap** for time-stamped logging or backup control
* **CAN bus support** for industrial applications
* **Thermal fuse + temp-triggered shutdown**
* **NV memory logging** for blackbox fault recording
* Add **EEPROM** or **FRAM** for configuration persistence
* **Digital potentiometers** to assist in analog rail tuning without discrete passives

### Firmware Ideas

* Integrate **PLD/FSM for low-latency reactions**
* Support **profiles/modes** (e.g., LowPowerMode, PerformanceMode)
* Implement **self-test** routines on boot
* Add **watchdog reset logic** for safety
* Develop **dynamic voltage scaling (DVS)** algorithms

### PSS\_API Ideas

* Provide **C++ and Rust wrappers** (optional)
* Integrate with **FreeRTOS or Zephyr hooks**
* Implement **auto-discovery** if multiple PSS modules exist
* Add **power budgeting features** (allocate power based on demand and priority)
---

## 📬 Contribution & License

We welcome open collaboration. Contributors can propose:

* New features
* Additional target MCU support
* Hardware revisions

> **License**: MIT / GPLv3 *(choose based on your project's philosophy)*

That’s a great decision — splitting the project into separate repositories for **hardware**, **firmware**, and **API** makes your Power Supply System (PSS) more modular, maintainable, and scalable, especially as it grows.

Here's how you can organize it effectively:

---

## 📂 Repository Structure Overview

| Repository Name | Purpose                                                      | Suggested README Title             |
| --------------- | ------------------------------------------------------------ | ---------------------------------- |
| `pss-hardware`  | Schematics, PCB layout, BOM, mechanical CAD                  | **Power Supply System – Hardware** |
| `pss-firmware`  | Co-processor firmware (encrypted OTA, Modbus, sensors, etc.) | **Power Supply System – Firmware** |
| `pss-api`       | High-level C API for main processor to interface with PSS    | **Power Supply System – Host API** |

