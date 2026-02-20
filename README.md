# Endovascular Sensor Readout - STM32 Firmware
## Overview
Redesigned the embedded data acquisition firmware for a multi-sensor endovascular guidewire designed to monitor blood flow dynamics in real-time. Ported the legacy control logic from an Arduino prototype to an STM32 microcontroller to leverage higher processing speeds, expanded memory, and advanced peripheral capabilities. Engineered the firmware to interface seamlessly with a newly designed custom PCB, optimizing the analog signal chain and eliminating previous hardware bottlenecks.

## Key Features
Architecture Optimization: Re-engineered the data acquisition topology to bypass the legacy multiplexed I2C bottleneck, ensuring reliable, synchronous sampling across 4 concurrent pressure sensor channels.

High-Throughput Acquisition: Configured STM32 hardware peripherals (Timers, external interrupts, and communication protocols) to manage continuous, high-speed micro-volt data streams without blocking the main execution loop.

Analog Chain Interfacing: Developed the control logic to interface with the optimized hardware signal path, ensuring clean data ingestion from the AD623 Instrumentation Amplifiers and MAX7403 8th-order Switched-Capacitor Filters.

Scalable Codebase: Built a modular Embedded C architecture to allow easy integration of future simultaneous-sampling ADCs (such as the ADS131M08) for scaling up to 10+ sensor channels.

## Hardware Components
STM32 Microcontroller

Custom Printed Circuit Board (KiCad)

AD623 Instrumentation Amplifiers

MAX7403 Switched-Capacitor Low-Pass Filters

High-Resolution ADC Modules

## Software Architecture
Developed the firmware in Embedded C using the STM32 Hardware Abstraction Layer (HAL). The software is driven by a non-blocking architecture where timer interrupts trigger sensor readings, and Direct Memory Access (DMA) can be utilized to transfer ADC payloads directly to memory. This approach ensures strict deterministic timing for the hemodynamic monitoring requirements.
