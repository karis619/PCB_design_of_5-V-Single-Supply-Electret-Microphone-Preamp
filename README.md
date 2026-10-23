# PCB_design_of_5-V-Single-Supply-Electret-Microphone-Preamp
This project brief describes how to build a compact, single-supply preamplifier module that converts the output of an electret microphone into a usable line-level audio signal.

# 5V Single-Supply Electret Microphone Preamplifier

This repository contains the PCB hardware design files (developed in EasyEDA Pro) for a compact, single-supply preamplifier module. The circuit converts the tiny AC current output of an electret microphone into a usable line-level audio signal. 

## Acknowledgment & Reference

This hardware layout is based directly on the circuit design, engineering analysis, and documentation published by **All About Circuits**. 

* **Reference Project:** [Building a 5V Single-Supply Electret Microphone Preamplifier](https://allaboutcircuits.com)
* **Original Circuit Author:** Robert Keim / All About Circuits

We gratefully acknowledge the original author and the All About Circuits community for providing the underlying schematic topology and comprehensive design theory used to build this PCB.

---

## Features & Technical Specifications

* **Operating Voltage:** 5 V DC
* **Output Voltage:** 1.2 V (centered symmetrically around mid-supply bias)
* **Frequency Response:** 20 Hz to 20 kHz (optimized audio passband)
* **Key Components:** Texas Instruments TLV6741 operational amplifier (SC70-5 package, 10 MHz, low noise)
* **Microphone Input:** PUI Audio Condenser Microphone capsule (MK1)
* **Interface Header:** 3-pin male header (Pitch: 2.54 mm) for power, ground, and line-out
* **Form Factor:** Extremely compact footprint measuring **22.54 mm x 8.26 mm**

---

## How the Circuit Works

1. **Signal Capture:** The electret microphone (`MK1`) generates an AC signal relative to ambient sound waves. 
2. **Coupling & Passband Filter:** Capacitor `C4` and resistor `R1` form a high-pass filter determining the low-end cutoff. Feedback components `R3` and `C3` control the amplifier gain and establish the upper high-frequency roll-off.
3. **Mid-Supply Biasing:** Resistors `R2` and `R5` create a resistor divider that references the non-inverting input at mid-supply (~1.2 V). This keeps the signal from clipping or experiencing input crossover distortion.
4. **Output Network:** Resistor `R4` and capacitor `C5` provide DC-blocking and downstream stage protection prior to the line output.

---

## Pinout Connections

The host connection is established through the **CN1** 3-pin connector terminal:

| Pin Number | Label | Description |
| :--- | :--- | :--- |
| **Pin 1** | `VCC` | +5 V DC Power Supply Input |
| **Pin 2** | `GND` | System Ground |
| **Pin 3** | `AUDIO` | Amplified Line-Level Audio Output Signal |

---

## Bill of Materials (BOM)

| Ref Des | Description | Qty | Manufacturer | Supplier Part No. |
| :--- | :--- | :--- | :--- | :--- |
| **CN1** | 3-pin male header, 2.54 mm pitch | 1 | Würth Elektronik | Digikey 732-5316-ND |
| **C1, C4**| 4.7 µF / 16 V Tantalum, 1206 | 2 | Kemet | Digikey |
| **C2** | 100 nF / 50 V Ceramic, 0805 | 1 | Yageo/Murata | Digikey |
| **C3** | 15 pF / 50 V Ceramic, 0805 | 1 | Yageo/Murata | Digikey |
| **C5, C6**| 3.3 µF / 16 V Tantalum, 1206 | 2 | Kemet | Digikey |
| **MK1** | Condenser Microphone Capsule | 1 | PUI Audio | Digikey 668-1197-ND |
| **R1** | 5.9 kΩ 1%, 0805 | 1 | Yageo/Murata | Digikey |
| **R2, R5**| 100 kΩ 5%, 0805 | 2 | Yageo/Murata | Digikey |
| **R3** | 75 kΩ 1%, 0805 | 1 | Yageo/Murata | Digikey |
| **R4** | 49.9 Ω 1%, 0805 | 1 | Yageo/Murata | Digikey |
| **R6** | 10 kΩ 5%, 0805 | 1 | Yageo/Murata | Digikey |
| **U1** | TLV6741 Op Amp, SC70-5 | 1 | Texas Instruments | Digikey 296-48176-1-ND |

---

## Manufacturing & Assembly Notes

* **Fabrication:** Gerber files can be exported straight from the EasyEDA Pro environment layout layout view (`Fabrication -> Gerber`).
* **Soldering:** Because the **SC70-5 package** (`U1`) and `0805` passives have a micro footprint, magnification tools or precise reflow/hot-air equipment are recommended during assembly. 
* **Microphone Mounting:** Solder the `MK1` microphone flush against the board edge to eliminate vibration-induced noise artifacts.

## License

This project is open-source hardware. See the repository's main profile page for licensing details.
