# edge-ai-iaq-monitor
Bare-metal Edge AI indoor air quality monitor &amp; predictor using Renesas CK-RA6M5 and ZMOD4410.
# Edge AI Indoor Air Quality Monitor & Predictor 

A bare-metal Indoor Air Quality (IAQ) monitor built on the Renesas CK-RA6M5 and ZMOD4410. The goal was to build a system that processes sensor data and runs simple AI inference locally on the MCU, avoiding the latency and dependency of cloud-based setups.

---

## Technical Highlights
* **Edge AI:** Executes a Multivariate Linear Regression model directly on the ARM Cortex-M33 core for real-time air quality forecasting.
* **Bare-Metal Firmware:** Register-level configuration for UART (SCI3) and GPIOs to minimize overhead and maximize execution speed.
* **Sensor Integration:** ZMOD4410 integration via I2C to capture TVOC and IAQ data.
* **Telemetry:** Real-time data streaming via UART (115200 baud) to a Python-based web dashboard.

---

## System Overview
The system architecture prioritizes autonomous operation. Instead of streaming raw data to the cloud, the CK-RA6M5 handles sensor polling, data processing, and AI inference locally.

### Key Components:
* **MCU:** Renesas CK-RA6M5 (ARM Cortex-M33 @ 200MHz, DSP/FPU).
* **Sensor:** ZMOD4410 (MOx technology for TVOC and eCO2 estimation).
* **Communication:** HW-597 USB-to-TTL module.
* **Visualization:** Custom Python backend serving a live web dashboard.

---

## 📸 Project Gallery


| Renesas CK-RA6M5 Kit | Web Dashboard Interface |
| :---: | :---: | 
| ![Hardware Kit](images/kit_ra6m5.png) | ![Dashboard](images/dashboard.png) |

---
## My Contributions
I focused on the **embedded firmware** and **getting the AI logic running directly on the hardware**.

I wrote the C driver for the ZMOD4410 sensor and used register-level programming for the UART and GPIO to keep the system fast and responsive. For the AI, I ported our linear regression model to C so it runs entirely on-chip—no cloud dependencies. I also managed the hardware bring-up, which involved plenty of debugging to iron out timing and signal issues to get a rock-solid data stream.



