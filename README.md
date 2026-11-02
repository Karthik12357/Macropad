# Custom USB Macropad

[![KiCad](https://img.shields.io/badge/EDA-KiCad%208-blue.svg)](https://kicad.org/)
[![MCU](https://img.shields.io/badge/MCU-Raspberry%20Pi%20RP2040-red.svg)](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v2.0-brightgreen.svg)](https://github.com/Karthik12357/Macropad/releases)

A customizable, programmable hardware macropad functioning as a USB HID device for rapid shortcut triggering, macro execution, and media control.

---

## 🚀 Version Evolution

### **Version 2.0 (Current: Discrete RP2040 Design in KiCad)**
The project has evolved from a dev-board breakout into a custom discrete hardware design centered around the **Raspberry Pi RP2040** microcontroller.

- **Microcontroller:** Raspberry Pi RP2040 (Dual-core ARM Cortex-M0+ running up to 133 MHz, 264 KB SRAM, 8 PIO state machines).
- **Power Management:** Dedicated on-board **NCP1117ST33** 3.3V low-dropout (LDO) linear regulator (SOT-223 package) converting 5V USB VBUS to a clean 3.3V system rail.
- **Clocking:** External 12.000 MHz SMD crystal oscillator (**ABM8-272-T3**) for USB clock stabilization.
- **USB Interface:** Reversible USB Type-C connector (**GCT USB4105-GF-A**) with 5.1 kΩ CC pulldowns for USB-C host negotiation.
- **EDA Suite:** Designed and routed in **KiCad 8**.
- **Architecture:** Hierarchical schematics separating top-level peripherals (`macropad.kicad_sch`) and MCU subsystem (`rp2040.kicad_sch`).

---

### **Version 1.0 (Legacy: Arduino Pro Micro Design in Altium)**
The initial iteration of the Macropad was constructed around the **Arduino Pro Micro (ATmega32U4)** dev board.

- **Grid:** 3×3 matrix of programmable mechanical key switches.
- **Analog & Controls:** 2 rotary encoders with pushbuttons and 1 sliding potentiometer for volume/slider adjustments.
- **Toolchain:** Designed in Altium Designer (`PCB1.PcbDoc`, `Sheet2.SchDoc`).
- 🏷️ **Legacy Access:** The full V1.0 Altium design files and history can be checked out anytime via git tag:
  ```bash
  git checkout v1.0
  ```
  or by browsing the [**v1.0 Release Tag**](https://github.com/Karthik12357/Macropad/tree/v1.0).

---

## 📁 Repository Structure

```text
Macropad/
├── macropad/                   # KiCad 8 hardware design (v2.0)
│   ├── macropad.kicad_pro      # KiCad project definition
│   ├── macropad.kicad_sch      # Top-level schematic
│   ├── rp2040.kicad_sch        # RP2040 microcontroller hierarchical sheet
│   ├── macropad.kicad_pcb      # PCB layout and routing
│   └── footprints.pretty/      # Project-specific component footprints
├── docs/                       # Official hardware design guides & datasheets
│   ├── RP-008279-DS-2-hardware-design-with-rp2040.pdf
│   └── RP-008371-DS-1-rp2040-datasheet.pdf
├── .gitignore                  # KiCad & OS file filters
└── README.md                   # Project documentation
```

---

## 🛠️ Hardware Specifications (v2.0)

| Subsystem | Component | Description / Specification |
| :--- | :--- | :--- |
| **Microcontroller** | Raspberry Pi RP2040 | Dual ARM Cortex-M0+, 133MHz, 264KB internal RAM |
| **Power Supply** | NCP1117ST33T3G | 3.3V, 1.0A LDO regulator (SOT-223) |
| **Connector** | GCT USB4105-GF-A | 16-pin USB Type-C (USB 2.0 full-speed) |
| **Oscillator** | Abracon ABM8-272-T3 | 12.000 MHz 10pF crystal oscillator |
| **Design Standard** | Raspberry Pi Hardware Specs | Compliant with official RP2040 hardware design guidelines |

---

## 💻 Firmware & Software Support (Planned / Compatible)
The RP2040 MCU allows flexible firmware options:
- **QMK / KMK:** Python-based or C-based programmable mechanical keyboard firmware.
- **Pico SDK / C++:** Bare-metal ultra-low latency USB HID implementation.
- **CircuitPython:** Rapid macro configuration with direct `.py` script editing over USB mass storage.

---

## 📄 License
This hardware design is released under the [MIT License](LICENSE).
