---
tags: [learning, flutter, mobile, dart]
topic: Flutter & Dart Mobile Development
category: Programming Languages & Frameworks
---

# 📱 Flutter Basics

## What Is It?

Flutter is Google's open-source UI software development kit (SDK) used to build natively compiled applications for mobile (Android & iOS), web, and desktop from a single codebase written in **Dart**.

Instead of wrapping native platform controls, Flutter renders its own UI directly on a canvas using a high-performance rendering engine (Impeller/Skia).

---

## Why Is It Important?

- **Single Codebase, Multiple Platforms:** Write code once and deploy to both Android and iOS devices.
- **Stateful Hot Reload:** See code changes instantly in the running app without losing your current app state.
- **Rich Widget Ecosystem:** Declarative, composable widgets allow rapid construction of polished, responsive interfaces.
- **First-Class Firebase Integration:** Seamless connectivity to Google Cloud, Firebase Firestore, Auth, and Cloud Messaging (FCM).
- **Strong Hardware/IoT Companion:** Ideal for building companion apps that interact with ESP32, Arduino, and IoT sensors over BLE or Wi-Fi.

---

## Core Dart & Flutter Concepts

### 1. Everything is a Widget
Flutter interfaces are built as a tree of widgets.

#### StatelessWidget (Immutable UI)
Use when the UI does not change based on user interaction or internal state.

```dart
import 'package:flutter/material.dart';

class FeederStatusCard extends StatelessWidget {
  final String status;
  final double batteryPct;

  const FeederStatusCard({
    super.key,
    required this.status,
    required this.batteryPct,
  });

  @override
  Widget build(BuildContext context) {
    return Card(
      elevation: 4,
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
      child: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text("Feeder Status: $status",
                style: const TextStyle(fontWeight: FontWeight.bold)),
            const SizedBox(height: 8),
            Text("Battery: ${batteryPct.toStringAsFixed(1)}%"),
          ],
        ),
      ),
    );
  }
}
```

#### StatefulWidget (Dynamic / Interactive UI)
Use when internal state changes over time (e.g., forms, toggles, animated counters).

```dart
class DispenseButton extends StatefulWidget {
  final VoidCallback onDispense;

  const DispenseButton({super.key, required this.onDispense});

  @override
  State<DispenseButton> createState() => _DispenseButtonState();
}

class _DispenseButtonState extends State<DispenseButton> {
  bool _isDispensing = false;

  void _triggerDispense() async {
    setState(() => _isDispensing = true);
    widget.onDispense();
    await Future.delayed(const Duration(seconds: 3));
    if (mounted) {
      setState(() => _isDispensing = false);
    }
  }

  @override
  Widget build(BuildContext context) {
    return ElevatedButton.icon(
      onPressed: _isDispensing ? null : _triggerDispense,
      icon: _isDispensing
          ? const SizedBox(
              width: 18,
              height: 18,
              child: CircularProgressIndicator(strokeWidth: 2))
          : const Icon(Icons.fastfood),
      label: Text(_isDispensing ? "Dispensing..." : "Dispense Now"),
    );
  }
}
```

---

## Working with Firebase & Streams

In IoT and real-time apps, Flutter connects to Firestore using `StreamBuilder` to receive instant updates whenever the ESP32 updates feeder telemetry:

```dart
StreamBuilder<DocumentSnapshot>(
  stream: FirebaseFirestore.instance
      .collection('feeders')
      .doc('feeder_01')
      .snapshots(),
  builder: (context, snapshot) {
    if (!snapshot.hasData) return const CircularProgressIndicator();
    var data = snapshot.data!.data() as Map<String, dynamic>;
    double currentWeight = (data['hopper_weight_grams'] ?? 0.0).toDouble();

    return Text("Current Hopper Feed: ${currentWeight.toStringAsFixed(0)}g");
  },
);
```

---

## Essential CLI Commands

```powershell
flutter doctor               # Check installed SDKs and Android toolchain
flutter pub get              # Install packages listed in pubspec.yaml
flutter run                  # Launch debug session on connected device / emulator
flutter run -d chrome        # Run in Chrome browser
flutter build apk --release  # Build production Android APK
```

---

## 🔗 Related Notes
- [[Automatic Dispensing System]]
- [[Embedded Systems and IoT]]
- [[Software Engineer Roadmap]]
- [[JavaScript Basics]]
- [[React Basics]]
