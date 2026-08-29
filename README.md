# Nexora_Veltraxx_26

## FPGA-Based Real-Time Vehicle Accident Detection and GPS-SMS Alert System

## 1. Project Overview

Our project is an FPGA-based real-time vehicle accident detection and alert system designed to identify potential accidents using **multi-sensor fusion** and automatically communicate the accident location.
Unlike simple impact-based systems, our project does not treat every shock as an accident. The system validates a potential impact using a **250 ms observation window** and a **70% impact-validation criterion**, followed by acceleration and speed-drop analysis.

The **FPGA** performs the real-time accident validation and decision-making, while an **ESP32** handles communication with the **NEO-6M GPS** and **SIM800L GSM** module.


# 2. Requirements

## Hardware

| Component                 | Purpose                         |
| ------------------------- | ------------------------------- |
| **Digilent Nexys 4 DDR**  | FPGA-based real-time processing |
| **ESP32**                 | Communication gateway           |
| **Impact / Shock Sensor** | Initial impact detection        |
| **MPU6050 IMU**           | Acceleration measurement        |
| **NEO-6M GPS**            | Location acquisition            |
| **SIM800L GSM**           | Emergency SMS                   |
| **Push Button**           | Manual collision-alert fallback |

## Software

### FPGA

* **Xilinx Vivado**
* Verilog HDL
* Nexys 4 DDR board support
* Verilog RTL simulator

### ESP32

* **Arduino IDE**
* ESP32 board support package
* Serial/UART communication support

# 3. Instructions

## A. FPGA Setup

1. Install **Xilinx Vivado**.
2. Create a new project for the **Nexys 4 DDR**.
3. Add the Verilog source files from the `FPGA/src` directory.
4. Add the testbench from `FPGA/simulation`.
5. Add the Nexys 4 DDR `.xdc` constraints file.
6. Run **RTL Simulation** to verify the design.
7. Run **Synthesis** and **Implementation**.
8. Generate the FPGA bitstream.
9. Connect the Nexys 4 DDR board.
10. Program the generated bitstream onto the FPGA.

## B. ESP32 Setup

1. Install **Arduino IDE**.
2. Install the ESP32 board package.
3. Open the Nexora ESP32 firmware.
4. Select the appropriate ESP32 board and COM port.
5. Configure the required UART pins.
6. Connect the FPGA UART output to the ESP32.
7. Connect the **NEO-6M GPS** to the ESP32.
8. Connect the **SIM800L GSM module** to the ESP32.
9. Upload the firmware.
10. Open the Serial Monitor and verify communication.

### Important

* Ensure all connected modules have a **common ground**.
* Verify the voltage requirements of each module before connecting it.
* Use a stable power supply for the **SIM800L**, as GSM transmission can require relatively high current.
* Verify the exact ESP32 board pinout before wiring.
* Do not directly connect signals without checking their voltage compatibility.

## D. RTL Simulation

The simulation should be used to verify:

* Accident FSM behavior
* Impact validation
* Risk classification
* UART telemetry
* Accident-event generation


The repository will be updated as the FPGA RTL, ESP32 firmware, hardware documentation, simulation files, and experimental results are added.
