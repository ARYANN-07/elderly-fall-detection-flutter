# 🛡️ Elderly Fall Detection System
### ESP32 Wristband + Flutter Android App

> *A smart wristband that automatically calls for help when an elderly person falls — even if they can't.*

---

## The Problem

Every year, millions of elderly people suffer falls that go unnoticed for hours — sometimes days. When no one is around to help, what should be a minor injury can become life-threatening.

This project solves that silent danger. The moment a fall is detected, family members receive an urgent SMS with a Google Maps location link — automatically, within seconds, without the elderly person needing to do anything.

No button to press. No app to open. No call to make. Just help, arriving before it's too late.

---

## Key Features

### ESP32 Wristband
- **Real-time Motion Sensing** — MPU6050 accelerometer monitors movements 24/7
- **On-device Fall Detection** — Two-stage algorithm: free-fall followed by sharp impact
- **Local Alerts** — Onboard buzzer sounds immediately on fall detection
- **Physical Cancel Button** — User can cancel false alarms within 10 seconds
- **Bluetooth Communication** — Talks to the Flutter app via Bluetooth Classic

### Flutter Android App
- **Bluetooth Connectivity** — Connects to ESP32-FallBand automatically
- **Real-time Status Monitoring** — Live connection and fall detection status
- **Emergency Contact Management** — Add/remove contacts from your phone's address book
- **Automated SMS Alerts** — Opens SMS app pre-filled with emergency message + location
- **GPS Location Sharing** — Google Maps link included in every alert
- **Follow-up Alerts** — Second SMS triggered after 60 seconds if not canceled
- **Remote Alarm Cancellation** — Cancel active alarm directly from the app

---

## Hardware Requirements

- ESP32 Development Board
- MPU6050 Accelerometer & Gyroscope Module
- Active or Passive Buzzer
- Push Button (for manual cancellation)
- Connecting Wires & Breadboard/PCB
- 5V Power Source (e.g. LiPo battery with charging circuit)

---

## Setup & Installation

### 1. ESP32 Wristband
1. Wire the MPU6050, buzzer, and button per the pin definitions in `Fall_detector.ino`
2. Install **Adafruit MPU6050** and **Adafruit Unified Sensor** libraries via Arduino Library Manager
3. Open `Fall_detector.ino`, select your ESP32 board and COM port, click **Upload**

### 2. Flutter App
1. Open the `fall_detection_flutter` folder in VS Code
2. Enable **Developer Options** and **USB Debugging** on your Android phone
3. Connect phone via USB, then run:
```bash
flutter pub get
flutter run
```
4. Grant all permissions when prompted (Bluetooth, Location, Contacts)

---

## How to Use

1. **Power On** — Power on the ESP32 wristband
2. **Pair Bluetooth** — In phone settings, pair with `ESP32-FallBand`
3. **Add Contacts** — Open app, tap **Add New Contact**
4. **Connect** — Tap **Connect** — status turns green
5. **Monitor** — App monitors 24/7. Fall detected → status card turns red
6. **Cancel** — Press wristband button or tap **CANCEL ALARM** within 10 seconds
7. **Alert** — If not canceled, SMS app opens pre-filled for all emergency contacts

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Firmware | Arduino C++ — ESP32 + BluetoothSerial |
| App | Flutter / Dart (Android) |
| Bluetooth | `flutter_blue_classic` (SPP/RFCOMM) |
| Location | `geolocator` |
| SMS | `url_launcher` (sms: URI scheme) |
| Contacts | `flutter_contacts` |
| Storage | `shared_preferences` |
