# 💡 Embedded Smart Light System (STM32 + FreeRTOS/HAL + Wokwi)

An embedded C firmware project running on an **STM32F401RE / Nucleo** target. The system acts as an automated ambient light monitor that dynamically toggles output status indicators using an **ADC-driven Light Dependent Resistor (LDR)** sensor, with complete hardware simulation integrated directly into VS Code via **Wokwi**.

---

## 🚀 Key Features

* **ADC Light Sensing:** Samples real-time ambient lighting levels using a photoresistor (LDR) on pin `PA0`.
* **Automatic Control Logic:** Toggles the room lighting indicator (`PA6`) on or off based on configurable lux thresholds.
* **System Heartbeat:** Periodically blinks a secondary status LED (`PA5`) using `HAL_Delay` hardware timers to signal active firmware execution.
* **Zero-Hardware Simulation:** Fully virtualized hardware testing environment inside VS Code using Wokwi—no physical board required.
* **CMake & GCC Toolchain:** Native ARM GCC cross-compilation pipeline with strict CMake build configurations.

---

## 🛠️ Hardware & Pin Configuration

| Component | Pin | Function |
| :--- | :--- | :--- |
| **Photoresistor (LDR)** | `PA0` | ADC1 Channel 0 Input (0–4095) |
| **System Heartbeat LED** | `PA5` | GPIO Output (Status / Diagnostic) |
| **Room Light LED** | `PA6` | GPIO Output (Actuator) |

---

## 💻 Software & Toolchain

* **Target Microcontroller:** STM32F401RE (ARM Cortex-M4)
* **Language:** C (C11 standard)
* **Hardware Layer:** STM32Cube Hardware Abstraction Layer (HAL)
* **Build System:** CMake + Ninja / Make
* **Compiler:** `arm-none-eabi-gcc`
* **Simulator:** Wokwi VS Code Extension

---

## 📂 Project Structure

```text
Smart-light-system/
├── Core/
│   ├── Inc/           # Header files (main.h, stm32f4xx_hal_conf.h)
│   └── Src/           # Firmware source code (main.c, stm32f4xx_it.c)
├── Drivers/           # STM32F4xx HAL and CMSIS driver libraries
├── CMakeLists.txt     # Main CMake build definition
├── wokwi.toml         # Wokwi simulator target mapping
├── diagram.json       # Interactive circuit schematic for Wokwi
└── README.md          # Project documentation