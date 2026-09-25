# EchoVolt: Predictive Maintenance Project

A lightweight, budget-conscious edge-computing system designed to track thermal gradients and detect mechanical bearing wear induced by rapidly fluctuating server workload surges. 

## Overview

EchoVolt uses a low-cost Raspberry Pi sensor node to continuously monitor server and rack health through two primary channels:

* **Acoustic Frequency Analysis:** Captures high-frequency noise shifts to identify early-stage mechanical bearing degradation in cooling fans.
* **Thermal Gradient Mapping:** Tracks heat distribution across components to catch abnormal hotspots, electrical connection faults, and airflow restrictions before they trigger catastrophic failures.

By processing data locally, EchoVolt targets persistent anomalies to prevent alarm fatigue and triggers automated alerts to keep critical infrastructure online.

## Architecture & Tech Stack

EchoVolt runs entirely at the edge on a Raspberry Pi sensor node.

* **Hardware:** Raspberry Pi Zero 2 W, Adafruit I2S MEMS Microphone, Adafruit MLX90640 Thermal Camera.
* **Languages & Libraries:** Python, SQLite (for lightweight local time-series history), NumPy/SciPy (for signal processing and rolling trends).
* **Interface:** Command-Line Interface (CLI) built for lightweight, headless execution and remote SSH management. 
* **Future Fleet Architecture:** Designed with a decoupled hub-and-spoke telemetry model in mind for future multi-node cellular gateway deployments.

## Hardware Procurement (Bill of Materials)
Before any assembly, research was conducted to select the lightest and most efficient components for a data center monitoring prototype.

### Controller
* **Raspberry Pi Zero 2 W:**
  * **Headless Architecture:** Configured for remote operation via SSH, eliminating the need for GUI/Monitor
  * **64-bit Architecture:** Running `Raspberry Pi OS Lite (64-bit)` to support data processing libraries.
  * **Multi-Sensor Interface:**
    * **I2C Bus:** Used for thermal sensor arrays
    *  **I2S Bus:** Used for acoustic data capture (microphone)
      
### Power Supply & Infrastructure
* **64GB SanDisk High-Endurance MicroSD card:** Selected to handle 24/7 data logging and many write cycles
* **UGREEN MicroSD Card Reader:** USB 3.0 for OS flashing from the ThinkPad.
* **CanaKit 5V/2.5A Power Cable**: Delivers a stable current to power the sensor node
  
### Physical Hardening & Assembly Kit
* **M2.5 Nylon Standoffs (6+6mm):** Non-conductive "feet" provide airflow and prevent electrical shorts against mounting surfaces.
*  **M2.5 Nylon Washers:** Added to the mounting stack for acoustic isolation (dampen mechanical vibrations from the environment).
*  **M2.5 Nylon Hex Nuts:** Secure the assembly at the top

### Sensor Array
* **SPH0645 I2S Microphone:**
  * MEMS acoustic sensor
  * **Purpose:** Captures high-frequency fan bearing noise for frequency analysis
* **MLX90640 IR Thermal Sensor:**
  * **Field of View:** 100° Wide Angle for full-rack monitoring
  *  **Purpose:** Provides a heat map of server motherboards, identifies component-level thermal anomalies
    
### Prototyping & Gear
* **Half-Sized Breadboard:** Compact design for mounting the acoustic and thermal sensors
* **40-Pin GPIO Header**: To be soldered to the Pi for sensor connectivity
* **Soldering Station & Assembly:**
  * Temperature controlled soldering iron with tips
  * Lead-free solder
  * Flux

### Connectivity & Interface Cables
* **StarTech USB-C to Micro_USB Adapter:** Data/power bridge between the ThinkPad X1 Carbon (USB-C) and the Sensor Node (Micro-USB).
*  **Jumper Wire Kit (M-M, M-F, F-F):** Wires used for testing and prototyping between the controller and breadboard

---
*Note: This repository serves as the system architecture specification and hardware bill of materials for EchoVolt. For a chronological breakdown of the development process, engineering decisions, and prototyping notes, check out the [LOG.md](./LOG.md) file. Core algorithmic processing scripts are maintained in a private workspace.*

 
