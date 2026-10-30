---
tags: [project, active, iot, mobile, hardware]
status: In Progress
type: Embedded IoT & Mobile Application
---

# 🐔 Smart Mobile-Based Solar-Powered Chicken Feeding System (Automatic Dispensing)

## Project Overview

| Field | Details |
|---|---|
| **Project Name** | Smart Mobile-Based Solar-Powered Chicken Feeding System |
| **Project Type** | IoT Embedded Hardware + Cross-Platform Mobile Application |
| **Description** | An automated, solar-powered poultry dispensing feeder featuring weight-based precision feeding, battery monitoring, and real-time mobile telemetry via Firebase. |
| **Problem Being Solved** | Poultry raisers struggle with inconsistent feeding schedules, feed waste, overfeeding/underfeeding, and inability to monitor feeding remotely or off-grid during power interruptions. |
| **Target Users** | Poultry farmers, agricultural researchers, backyard chicken raisers |
| **Current Status** | In Progress (Firmware calibrated, Flutter app under active development) |
| **Start Date** | 2026 |
| **Deadline** | Capstone / Project Milestone |
| **Team Members** | Jehosue Biscarra (Lead Developer, Firmware Engineer & Mobile App Architect) |
| **Client / Organization** | Academic Capstone / Agricultural IoT Initiative |
| **Tech Stack** | Flutter (Dart), ESP32 (C++/PlatformIO/Arduino), Firebase (Auth, Firestore, Cloud Messaging), Solar Power Circuitry |
| **Repository** | [GitHub: Jehooooo/SMART-MOBILE-BASED-SOLAR-POWERED-CHICKEN-FEEDING-SYSTEM](https://github.com/Jehooooo/SMART-MOBILE-BASED-SOLAR-POWERED-CHICKEN-FEEDING-SYSTEM.git) |
| **Local Path** | `C:\Users\Jeho\Documents\AutomaticDispensing` |

---

## 🎯 Project Goals

### Main Goal
Develop an off-grid, solar-powered automated feeding system that dispenses poultry feed according to programmed schedules and exact weights, controllable and monitorable anywhere via an Android mobile app.

### Core Features
- [ ] **Weight-Based Precision Dispensing:** HX711 load cell sensor integration for real-time gram-level dispensing accuracy.
- [ ] **Solar Power & Battery Autonomy:** Solar panel with TP4056/BMS charge controller and 18650 Li-ion battery pack for off-grid operations.
- [ ] **Cross-Platform Mobile App (Flutter):** Modern mobile UI for scheduling, telemetry, and manual dispensing triggers.
- [ ] **Cloud Synchronization (Firebase):** Bidirectional real-time syncing of feeding logs, schedule timers, and feeder telemetry.
- [ ] **Push Notification Alerts:** Low feed hopper alert, battery level warnings, and dispensing confirmation notifications.
- [ ] **Manual Override:** One-tap emergency feeding button from the mobile app and physical button on device.
- [ ] **Offline Redundancy:** On-chip RTC/timer scheduling on ESP32 in case Wi-Fi connectivity drops.

### Minimum Viable Product (MVP)
- Functional ESP32 firmware running stepper/servo motor based on weight feedback from HX711.
- Solar battery charging circuit powering ESP32 and motor driver continuously.
- Flutter mobile app communicating with Firebase to set schedule times and target feeding weight.
- Notification dispatch when feed level falls below threshold.

---

## 🔧 Architecture & Subsystems

```
┌───────────────────────────────────────────────┐
│              Solar Power System               │
│  [Solar Panel] ──> [Charge Controller] ──> [18650 Battery Pack]
└───────────────────────┬───────────────────────┘
                        │ (Power Bus)
                        ▼
┌───────────────────────────────────────────────┐
│               ESP32 Controller                │
│  - Load Cell (HX711) for Weight Sensing        │
│  - Motor Driver (A4988 / Servo) for Feeder    │
│  - Wi-Fi Telemetry & Local Fail-Safe Schedule  │
└───────────────────────┬───────────────────────┘
                        │ (Internet / Wi-Fi)
                        ▼
┌───────────────────────────────────────────────┐
│             Firebase Cloud Platform           │
│  - Authentication                             │
│  - Cloud Firestore / Realtime DB              │
│  - Cloud Messaging (FCM Alerts)               │
└───────────────────────┬───────────────────────┘
                        │
                        ▼
┌───────────────────────────────────────────────┐
│              Flutter Mobile App               │
│  - Feeder Dashboard & Live Hopper Status      │
│  - Custom Schedule Configuration              │
│  - Feeding Logs & Analytics                   │
└───────────────────────────────────────────────┘
```

---

## ✅ Tasks & Milestones

### Firmware & Hardware (ESP32)
- [x] Set up PlatformIO project with Arduino framework
- [x] Configure Wi-Fi manager and Firebase ESP Client library
- [x] Calibrate HX711 load cell amplifier with known weights
- [x] Implement motor actuation logic (start motor, monitor weight target, stop motor)
- [x] Implement battery voltage divider circuit for charge percentage calculation
- [ ] Implement deep sleep / low power modes between scheduled feeding windows

### Mobile App (Flutter)
- [x] Set up Flutter project structure and Android build settings
- [x] Integrate Firebase Auth and Firestore dependencies
- [x] Build dashboard screen with live hopper gauge and battery status
- [ ] Build schedule management screen (add, edit, toggle feeding intervals)
- [ ] Implement manual dispensing button with confirmation modal
- [ ] Set up Firebase Cloud Messaging (FCM) background handler for notifications
- [ ] Add historical feeding logs with daily/weekly consumption charts

### Documentation & Methodology
- [x] Author methodology and system architecture (`docs/methodology_analysis.md`)
- [x] Generate Gantt chart timeline (`gantt_chart_timeline.png`)
- [ ] Conduct field trial and capture accuracy/weight deviation metrics

---

## 💻 Tech Stack & Dependencies

| Layer | Component | Notes |
|---|---|---|
| **Mobile Client** | Flutter 3.x (Dart) | Tested on Android, running via `flutter run` |
| **State Management** | Provider / Riverpod | Reactive UI updates on telemetry change |
| **Cloud Backend** | Google Firebase | Firestore, Firebase Auth, FCM |
| **Microcontroller** | ESP32-WROOM-32 | Dual-core, Wi-Fi 802.11 b/g/n, Bluetooth |
| **Firmware Toolchain** | PlatformIO (`uv tool install platformio`) | C++ with Arduino core |
| **Sensory** | HX711 + Strain Gauge Load Cell | 5kg load cell for food bowl / hopper |
| **Actuator** | Stepper / Continuous Servo | Auger screw or sliding gate dispenser |

---

## 🔗 Related Notes
- [[Flutter Basics]]
- [[Embedded Systems and IoT]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
- [[Resume and Portfolio]]
- [[Software Engineer Roadmap]]
