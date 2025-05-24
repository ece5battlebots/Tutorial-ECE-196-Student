# ESP32 Digital Privacy Window Controller

This project demonstrates how to use an ESP32 DevBoard to control a **digital privacy window** (such as an electrochromic or liquid crystal film) using voltage. By toggling a GPIO pin, the ESP32 can switch the window between **transparent** and **opaque** states, enabling dynamic control for privacy or solar heat management.

## 🔧 Features
- GPIO-controlled switching of privacy window film
- Works with 3.3V logic (ESP32) and higher voltage glass (via relay or MOSFET)
- Expandable: Wi-Fi control, mobile app integration, automation with sensors

## 🧰 Materials Required
- ESP32 Development Board (e.g., ESP32-WROOM-32)
- Electrochromic or liquid crystal privacy film
- Power source (typically 12V for film)
- N-channel MOSFET (e.g., IRFZ44N) or relay module
- Diode (e.g., 1N4007, if using a relay)
- Jumper wires and breadboard
- Optional: temperature/light sensors, Wi-Fi interface

## 🔌 Wiring Overview
| ESP32 Pin | Component           | Description                    |
|-----------|---------------------|--------------------------------|
| GPIO25    | MOSFET Gate / Relay | Controls power to window film |
| VIN/3.3V  | Relay VCC           | ESP32 power (relay logic)      |
| GND       | Common Ground       | Shared with MOSFET/relay/glass |

> ⚠️ **Note:** Ensure your switching device (MOSFET or relay) can handle the voltage/current required by the privacy window film.

## 📦 How It Works
The ESP32 outputs a digital HIGH or LOW on a GPIO pin to control a switching device (MOSFET or relay). This device then supplies or cuts off voltage to the privacy glass.

## 🧠 Example Code
```cpp
int controlPin = 25;

void setup() {
  pinMode(controlPin, OUTPUT);
}

void loop() {
  digitalWrite(controlPin, HIGH); // Opaque
  delay(5000);
  digitalWrite(controlPin, LOW);  // Transparent
  delay(5000);
}
