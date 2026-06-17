# EUROBOT 2026 — SCRAT PCB development
## Overview

**Welcome to the PCB development repository for the SCRAT robot of the Engi-Teams team for the Eurobot 2026 competition.** This project encompasses the complete PCB development for the SCRAT robot, including power distribution, control logic, and interface routing. The hardware architecture is built around the STM32H723VGT6 microcontroller (ARM Cortex-M7, 550 MHz) and features two dedicated boards — a Power Board and a Control Board. The design provides multiple regulated voltage rails ***(3.3 V, 5 V, 12 V, 24 V, and adjustable output)***, battery protection circuitry, ESD protection, and EMI filtering. Communication with the high-level PC stack is routed via USB CDC (HS) through micro-ROS‑compatible interfaces. To ensure high quality and stable operation of the robot, the complete PCB development cycle was divided into 10 main stages:


**`1`** Electronic Components Selection (ECS)  
**`2`** Incoming Inspection & Component Testing  
**`3`** Schematic Design  
**`4`** PCB Layout Design  
**`5`** Design Rule Verification (DRC, LVS)  
**`6`** Manufactured PCB Testing  
**`7`** Complete Assembly of All Electronic Modules  
**`8`** Electrostatic Discharge (ESD) Testing  
**`9`** Electromagnetic Compatibility (EMC) Testing  
**`10`** Final System Testing
## Repository Structure



├── BOM/
│ └── Bill of Materials with procurement links
├── CAD/
│ ├── schematic/ # Electrical schematics
│ ├── library/ # Component library elements
│ ├── layout/ # PCB layout files
│ ├── rules.rul # Design rules
│ └── stackup/ # Layer stackup with materials and thicknesses
├── Docs/
│ ├── STM32H723VGT6/ # Microcontroller documentation
│ └── tools/ # Design tools list
├── Firmware/
│ └── pinout/ # Control board pinout description
├── Gerber/
│ └── Manufacturing files
├── Mech/
│ ├── boards/ # 3D PCB models (.step)
│ └── components/ # 3D component models
└── Reports/
├── photos/ # Testing photos
└── docs/ # Engineering documentation (.pdf)

---

## Key Technical Solutions

### 1. Magnetic Mounting for DC-DC Converters
Magnetic mounting for DC-DC converters enables quick module replacement in case of overheating or failure. This solution significantly simplified assembly, debugging, and reduced repair time.

### 2. Comprehensive Power Supply System
Implemented voltage rails:
- 3.3 V
- 5 V
- 12 V
- 24 V
- Adjustable voltage from 3.3 to 24 V

This solution allows powering sensors, servos, motors, and other robot modules with different voltage requirements. The adjustable rail serves as a backup for connecting modules with non-standard supply voltages.

### 3. Battery Deep Discharge Protection
An integrated battery discharge control circuit disconnects the battery when the voltage drops below a user-adjustable threshold (set via potentiometer), protecting the battery from over-discharge.

### 4. Power and Logic Separation
To reduce noise coupling from power circuits to sensitive interface nodes, the power and low-voltage sections were separated into two distinct boards:
- Power Board
- Control Board

### 5. Independent Debugging
The ability to debug each board independently simplified the tuning of electronic modules inside the robot.

### 6. Redundant Interfaces
In addition to the main interfaces, the control board features expansion connectors for connecting additional sensors, actuators, and modules with interfaces not originally planned.

### 7. Overvoltage and ESD Protection
Built-in overvoltage and electrostatic discharge protection ensures the safety of sensitive components.

### 8. Switchable Filtering System
The power board implements a switchable filtering system using a capacitor array on each power rail, reducing the impact of internal power supply noise on the control board nodes.

---

## Manufacturing and Assembly

- **Fabrication:** Resonit factory (Moscow, Russia)
- **Soldering:** In-house laboratory
- **Connectors:** XH2.54 and pin headers for fast and reliable connections
- **Indication:** LED indicators for visual status monitoring of key modules

### Assembled Board Photos
> *Images of the assembled boards*

- [Power Board Photo](Reports/photos/power_board.jpg)
- [Control Board Photo](Reports/photos/control_board.jpg)

---

## Testing

### Laboratory Test Bench
A temporary laboratory test bench was assembled for PCB testing, equipped with:
- Oscilloscope
- Multimeter
- Power supply
- Signal analyzer
- Function generator

### Testing Photos
- [Power Board Testing](Reports/photos/power_test.jpg)
- [Control Board Testing](Reports/photos/control_test.jpg)

---

## Protection and Noise Immunity

### Grounding
To enhance reliability and protect against static electricity:
- Both boards are connected to the common robot chassis
- Grounding is provided through a dedicated metal contact at the bottom of the housing
- Motor power circuits are additionally grounded

These measures eliminate potential breakdowns and interference, significantly increasing system fault tolerance.

### Shielding and Noise Suppression
- All signal lines are implemented as twisted pairs to reduce crosstalk
- Critical nodes underwent clock frequency optimization (reduced to minimum acceptable values without affecting performance)

### Protection Measures
- Proper shielding
- Signal buffering
- Well-designed grounding scheme

---

## Results

Final testing confirmed the high reliability of the system — the robot started successfully on the first attempt, demonstrating flawless operation of all modules.

This result was achieved through:
- Thorough design
- Step-by-step debugging
- Comprehensive implementation of protective measures

### Robot Integration Photo
> *Image of the boards installed in the robot*

- [Boards in Robot](Reports/photos/robot_assembly.jpg)

---

## Contact

For collaboration inquiries and additional information, please contact the project developers.

---

**© 2026 | Project developed as part of a robotics system creation**
