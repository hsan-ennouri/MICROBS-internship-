# Endovascular Sensor Readout - STM32 Firmware
## Overview
Redesigned the embedded data acquisition firmware for a multi-sensor endovascular guidewire designed to monitor blood flow. Migrated the code from an Arduino prototype to an STM32 microcontroller to leverage higher processing speeds, expanded memory, and advanced peripheral capabilities. Engineered the firmware to interface with a newly designed custom PCB, optimizing the analog signal chain.

## Key Features
Architecture Optimization: Re-engineered the data acquisition topology to bypass the legacy multiplexed I2C bottleneck, ensuring reliable, sampling across 4 concurrent pressure sensor channels.

High-Throughput Acquisition: Configured STM32 hardware peripherals (Timers, external interrupts) to manage continuous, high-speed micro-volt data streams without blocking the main execution loop.

Analog Chain Interfacing: Developed the control logic to interface with the optimized hardware signal path, ensuring clean data ingestion from the AD623 Instrumentation Amplifiers and MAX7403 8th-order Switched-Capacitor Filters.

## Hardware Components
STM32 Microcontroller

Custom Printed Circuit Board (KiCad)

AD623 Instrumentation Amplifiers

MAX7403 Switched-Capacitor Low-Pass Filters

Analog to Digital Converter : ADS1115 

## Software Architecture
Developed the firmware in Embedded C using the STM32 Hardware Abstraction Layer (HAL). The software is driven by a non-blocking architecture where timer interrupts trigger sensor readings. This approach ensures strict deterministic timing for the hemodynamic monitoring requirements.
