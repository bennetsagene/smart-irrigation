# 🌱 Arduino Smart Irrigation System

An automated plant irrigation system built with an Arduino Uno that monitors soil moisture levels and activates a water pump when the soil is too dry — eliminating the need for manual watering.

> **Status:** Concept & Design Phase — hardware design and logic completed; physical build in progress.

---

## 📋 Overview

Manual watering is inconsistent and often leads to either overwatering or underwatering plants. This project addresses that by using a soil moisture sensor to continuously monitor conditions and automatically triggering a relay-controlled water pump only when needed.

The system also displays real-time moisture readings on an LCD screen, giving the user visibility into soil conditions at a glance.

---

## ⚙️ Components

| Component | Purpose |
|---|---|
| Arduino Uno | Main microcontroller — reads sensors and controls outputs |
| Soil Moisture Sensor | Detects soil water content and sends analog signal to Arduino |
| Relay Module | Acts as a switch to safely control the water pump from Arduino |
| Water Pump (DC) | Delivers water to the plant when triggered by the relay |
| LCD Display (16x2) | Shows live soil moisture readings and pump status |
| Jumper Wires & Breadboard | Prototyping and circuit connections |

---

## 🔧 How It Works

1. The **soil moisture sensor** continuously reads the water content of the soil and sends an analog voltage to the Arduino.
2. The Arduino compares the reading against a **predefined moisture threshold**.
3. If the soil is **too dry** (reading below threshold), the Arduino activates the **relay module**, which switches on the water pump.
4. The pump runs until the moisture level rises above the threshold, at which point the relay cuts power to the pump.
5. The **LCD display** shows the current moisture value and whether the pump is ON or OFF in real time.

---

## 🗂️ Project Structure

```
smart-irrigation/
├── README.md
├── src/
│   └── irrigation.ino       # Main Arduino sketch
├── circuit/
│   └── wiring_diagram.png   # Circuit diagram (coming soon)
└── docs/
    └── project_report.pdf   # Design report (coming soon)
```

---

## 💻 Core Logic (Pseudocode)

```cpp
int moistureValue = analogRead(MOISTURE_SENSOR_PIN);

if (moistureValue < DRY_THRESHOLD) {
    // Soil is dry — activate pump
    digitalWrite(RELAY_PIN, HIGH);
    lcd.print("Pump: ON");
} else {
    // Soil is moist enough — keep pump off
    digitalWrite(RELAY_PIN, LOW);
    lcd.print("Pump: OFF");
}

// Display live reading on LCD
lcd.print("Moisture: ");
lcd.print(moistureValue);
```

---

## 🚀 Getting Started

### Prerequisites
- [Arduino IDE](https://www.arduino.cc/en/software) installed
- `LiquidCrystal` library (included with Arduino IDE by default)

### Upload the Code
1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/smart-irrigation.git
   ```
2. Open `src/irrigation.ino` in the Arduino IDE.
3. Connect your Arduino Uno via USB.
4. Select **Tools > Board > Arduino Uno** and the correct COM port.
5. Click **Upload**.

---

## 📌 Planned Improvements

- [ ] Add a timer to prevent overwatering even if sensor malfunctions
- [ ] Log moisture data over time using an SD card module
- [ ] Add a manual override button
- [ ] Explore solar power for off-grid use

---

## 👤 Author

**Bennet Enifa Sagene**  
Hardware Engineering Student — University of Zimbabwe  
📧 bennetsagene@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/bennet-sagene-76a096376)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
