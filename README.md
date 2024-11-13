# Custom-NRF24l01-Board
## Overview
This repository contains files and documentation for a custom NRF24L01 board.  The board uses an NRF24L01 chip for low power wireless applications.

## Features
Custom PCB Design: Tailored board layout for optimized performance with the NRF24L01 module.
Compact and Efficient: Designed to minimize space and power usage.
Compatibility: Works with common microcontrollers such as Arduino, STM32, and ESP32.

## Power Filters
**Capacitors (C7, C8, C9):** These capacitors (33nF, 10nF, and 1nF) are used for power supply decoupling. They filter out noise and stabilize the power line to the nRF24L01+.
- Different capacitors can filter different noises, and the use of (33nF, 10nF, and 1nF) capacitors can cover a wide range of noises
- Formula: E = (1/2)CV^2
    - E: energy stored in a capacitor
    - C is the capacitance in farads (F)
    - V is the voltage across the capacitor.
**Resistor (R2):** A 22kΩ resistor used as a pull-up for the VDD line, providing stability to the power supply input.
### Crystal Oscillator Circuit (X1, C1, C2, R1)
**Crystal (X1):** A 16 MHz crystal provides a stable clock frequency for the nRF24L01+.
**Capacitors (C1, C2):** These 22pF capacitors are connected to ground and they establishes a balanced resonant condition, allowing the crystal to oscillate accurately at 16 MHz.

**Resistor (R1):** A 1MΩ resistor across the crystal to ensure proper startup of the oscillator circuit.
### RF Network (L1, L2, L3, C3, C4, C5, C6)
**Inductors (L1, L2, L3):** These inductors (8.2nH, 2.7nH, 3.9nH) are part of a matching network, helping to match the impedance of the nRF24L01+ output to the antenna.
**Capacitors (C3, C4, C5, C6):**
- C3 and C4 (2.2nF and 4.7pF): Used to filter and stabilize the RF signal.
- C5 (1.5pF) and C6 (1.0pF): Part of the antenna matching circuit to optimize RF performance.
- 50Ω Antenna Port: The network ends with a 50Ω impedance port, which is typical for RF antenna matching to ensure efficient signal transmission and reception
The main function of the nRF24L01+ chip is **wireless communication**
- **VDD:** power
- **VSS:** gound
- **DVDD:** internal digital supply output for de-coupling purpose
- **VDD_PA:** Power supply for the internal power amplifier. (must connect to ANT1 and ANT2)
- **ANT1 and ANT2:** Connections to the antenna network, allowing for the transmission and reception of RF signals.
- **XC1 and VC2:** Crystal pin
- **IREF:** reference current
- **CE (chip enable):** Controls data transmission or reception. High to enable the transceiver, and low to put it on standby.
- **CSN (SPI Chip Select):** Used to select the nRF24L01+ for SPI communication. Set low to enable SPI communication.
    - SPI communication: communication protocol used to transfer data between a master device and slave devices 
- **SCK (Serial Clock), MOSI, MISO:** These are SPI pins used for communication with a microcontroller or host device.
- **IRQ:** Interrupt request pin to signal the host of certain events, like data received or transmitted.

## Datasheet and Resources
https://www.sparkfun.com/datasheets/Components/SMD/nRF24L01Pluss_Preliminary_Product_Specification_v1_0.pdf
https://en.wikipedia.org/wiki/Impedance_matching


