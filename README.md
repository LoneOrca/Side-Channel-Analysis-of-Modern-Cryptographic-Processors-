---
# Side Channel Analysis of Modern Cryptographic Processors

This repository contains the research and practical implementation of hardware-level security analysis, focusing on **firmware extraction** and **Side-Channel Analysis (SCA)**. The project demonstrates how hardware vulnerabilities can lead to the recovery of secret cryptographic keys from embedded devices.

##  Project Overview

Modern security often focuses on software, but the physical hardware executing that software can "leak" information. This project explores two main attack vectors:

1. **Firmware Extraction & Key Recovery:** Accessing the "brain" of an IoT device to find hidden encryption keys.

2. **Differential Power Analysis (DPA):** Using power consumption patterns to extract AES keys from microcontrollers without physical tampering.


## Tools & Technologies

### Hardware

* **Target Devices:** STM32F303, Atmel XMEGA, and TP-Link Wireless Router.
* **Extraction Tools:** CH341a ROM Programmer, SOIC8 Clip, and Logic Analyzers.
* **SCA Platform:** ChipWhisperer (for power analysis).

### Software

* **Analysis:** Ghidra (Reverse Engineering), Binwalk (Firmware Analysis).
* **Signal Visualization:** PulseView / Sigrok.
* **Utilities:** Flashrom.

##  Key Experiments

### 1. Firmware Extraction

By connecting a CH341a programmer to the EEPROM of a TP-Link router via SPI, the raw binary firmware was extracted.

* **Result:** Using Ghidra to analyze the decompiled C code, the DES decryption key was successfully located within the firmware.

### 2. Differential Power Analysis (DPA)

This phase focused on monitoring the minute changes in power consumption while a processor (STM32/XMEGA) performed AES encryption.

* **Result:** By analyzing power traces, the AES encryption keys were recovered by exploiting hardware-level information leakage.

##  Recommended Countermeasures

The findings of this research advocate for stronger silicon-level defenses:

* **Secure Boot:** Ensures only authenticated firmware runs.
* **Key Masking:** Hides sensitive data in power traces.
* **Power Balancing:** Makes power consumption uniform to prevent DPA.

##  Academic Context

This work was submitted as a Master’s Thesis in Electrical Engineering at **Western New England University** (May 2025).

* **Author:** Srinivas Nittala.

* **Advisor:** Prof. Love K. Sah, Ph.D..
* **Link:** https://digitalcommons.law.wne.edu/coetheses/24/


---

*Disclaimer: This project is for educational and research purposes only. Always obtain permission before testing the security of any device.*
