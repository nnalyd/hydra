# High-Precision Analog Data Acquisition System (Hydra)

**Type:** Modular Mixed-Signal PCB Stack
**CAD Tool:** KiCad 9.0

## System Overview
This repository contains the hardware design files for a modular data acquisition platform. The system is designed to evaluate different ADC architectures for ultra-low latency Hall Effect sensing (target: 0.005mm displacement accuracy).

The architecture uses a **split-plane vertical stackup**:
1.  **Base Layer (Main Board):** Handles power regulation, USB communication, and digital processing.
2.  **Mezzanine Layer (Modules):** Interchangeable analog front-ends that isolate sensitive signal paths from digital switching noise.

## The Modules

### 1. Main Control Board (Base)
* **MCU:** NXP LPC55S69 (Dual-core Cortex-M33)
* **Key Design Features:**
    * **Power Architecture:** Low-noise LDO stage to provide clean 3.3V and 5V references to the mezzanine headers.
    * **Interface:** High-speed SPI interconnect routed to mezzanine connectors.
    * **Physical:** Mounting points for secure mechanical stacking, in the form of a keyboard as a functional test device.

### 2. Module A: "Precision" Architecture
* **Core Silicon:** TI ADS8568 (16-bit SAR ADC)
* **Design Goal:** High-Precision ADCs for very accurate readings.

### 3. Module B: "Distributed" Architecture
* **Core Silicon:** TI MSPM0G3507 (Arm Cortex-M0+)
* **Design Goal:** Distributed processing experiment with internal ADCs.
