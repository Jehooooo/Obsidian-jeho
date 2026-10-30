---
tags: [learning, embedded, iot, esp32, arduino, hardware]
topic: Embedded Systems & IoT Engineering
category: Hardware & Embedded Software
---

# ⚡ Embedded Systems and IoT

## What Is It?

Embedded systems combine dedicated microcontrollers with software firmware to perform specific control and monitoring tasks in physical devices. 

The **Internet of Things (IoT)** extends embedded systems by connecting physical sensors and actuators to cloud services (like Firebase or MQTT brokers) and mobile applications for remote monitoring and automation.

---

## Why Is It Important?

- **Real-World Impact:** Interfacing software with physical mechanics (dispensers, motors, relays, environmental sensors).
- **Edge Intelligence:** Performing measurements, calibrations, and safety cutoffs directly on-device without needing internet connectivity.
- **Resource Constraints:** Writing memory-efficient C/C++ code managing limited RAM (520 KB on ESP32), clock cycles, and battery power.
- **High Demand:** Crucial for Smart Agriculture, Industrial Automation, Smart Home, and Robotics.

---

## Key Hardware Components

### 1. ESP32 Microcontroller
- **Specs:** 32-bit dual-core Xtensa @ 240MHz, 520 KB SRAM, 4MB Flash.
- **Connectivity:** 2.4 GHz Wi-Fi (802.11 b/g/n) and Bluetooth (v4.2 BR/EDR and BLE).
- **Peripherals:** 12-bit ADCs, DACs, I2C, SPI, UART, PWM, capacitive touch sensors.
- **Power Efficiency:** Multiple sleep modes (Active, Modem Sleep, Light Sleep, Deep Sleep down to ~10 µA).

### 2. HX711 Load Cell Amplifier
- 24-bit analog-to-digital converter designed specifically for weigh scales.
- Reads microvolt variations from strain gauge Wheatstone bridges.
- Requires calibration with known calibration weights (`scale.set_scale(factor)` and `scale.tare()`).

### 3. Actuators: Motors & Servos
- **Stepper Motors (NEMA 17 + A4988 driver):** Exact positional control and rotational steps for dispensing screw augers.
- **Servo Motors:** Angle-based PWM positioning for hopper flaps and gates.

### 4. Solar Power & Battery Subsystem
- **Solar Panel:** 6V / 12V photovoltaic array.
- **Charge Controller / BMS:** Regulates battery charging from solar power and prevents over-discharge.
- **Voltage Divider:** Scaled voltage reading fed into an ADC pin to monitor battery percentage safely.

---

## Essential C++ / PlatformIO Code Patterns

### 1. Non-Blocking Execution with `millis()`
Never use `delay()` in production IoT firmware as it halts all Wi-Fi, sensor polling, and network heartbeats.

```cpp
#include <Arduino.h>

unsigned long previousMillis = 0;
const long interval = 5000; // 5 seconds interval

void loop() {
  unsigned long currentMillis = millis();

  if (currentMillis - previousMillis >= interval) {
    previousMillis = currentMillis;
    // Perform scheduled task (e.g., read weight, sync with cloud)
    checkTelemetry();
  }

  // Other tasks run without blocking
}
```

### 2. Reading HX711 Load Cell
```cpp
#include "HX711.h"

const int LOADCELL_DOUT_PIN = 16;
const int LOADCELL_SCK_PIN = 4;

HX711 scale;

void setup() {
  Serial.begin(115200);
  scale.begin(LOADCELL_DOUT_PIN, LOADCELL_SCK_PIN);
  scale.set_scale(2280.f); // Calibration factor obtained from test weights
  scale.tare();            // Reset scale to 0
}

void loop() {
  if (scale.is_ready()) {
    float weightGrams = scale.get_units(5); // Average of 5 readings
    Serial.printf("Weight: %.2f g\n", weightGrams);
  }
}
```

---

## PlatformIO Toolchain Cheatsheet

```powershell
# Build firmware
pio run

# Upload to connected ESP32 via COM port
pio run -t upload

# Open Serial Monitor (default baud 115200)
pio device monitor

# Combined upload and serial monitor
pio run -t upload -t monitor
```

---

## 🔗 Related Notes
- [[Automatic Dispensing System]]
- [[Flutter Basics]]
- [[Python Basics]]
- [[Software Engineering]]
