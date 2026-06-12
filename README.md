# Arduino Smart Irrigation System

A soil moisture-based irrigation system designed using an Arduino Uno. The idea is simple — instead of watering plants manually and guessing whether the soil is dry or not, the system checks the moisture level automatically and only runs the pump when needed.
Status: Design and planning phase. Components identified, circuit designed, code logic worked out. Physical build is the next step.
---
The Problem
I noticed that plants are often either overwatered or underwatered because there's no consistent way to check soil conditions manually. This project is an attempt to solve that using basic sensor input and relay control.
---
Components
Component	Purpose
Arduino Uno	Main microcontroller
Soil Moisture Sensor	Reads water content in the soil
Relay Module	Controls the pump safely from the Arduino
Water Pump (DC)	Pumps water when soil is dry
LCD Display (16x2)	Shows current moisture level and pump status
Jumper Wires & Breadboard	Circuit connections for prototyping
---
How It Works
The moisture sensor sends an analog reading to the Arduino. If the reading falls below a set threshold (meaning the soil is dry), the Arduino triggers the relay, which switches the pump on. Once the moisture level recovers, the pump switches off. The LCD shows what's happening in real time.
The threshold value can be adjusted in the code depending on the plant type.
---
Core Logic
```cpp
int moistureValue = analogRead(MOISTURE_SENSOR_PIN);

if (moistureValue < DRY_THRESHOLD) {
    digitalWrite(RELAY_PIN, HIGH);  // turn pump on
    lcd.print("Pump: ON");
} else {
    digitalWrite(RELAY_PIN, LOW);   // turn pump off
    lcd.print("Pump: OFF");
}

lcd.print("Moisture: ");
lcd.print(moistureValue);
```
---
What I Want to Add Later
A timer so the pump doesn't run too long even if the sensor gives a bad reading
Data logging to track moisture levels over time
A manual override button
Possibly a solar power setup for outdoor use
---
Project Structure
```
smart-irrigation/
├── README.md
├── src/
│   └── irrigation.ino
├── circuit/
│   └── wiring_diagram.png   (coming soon)
└── docs/
    └── project_report.pdf   (coming soon)
```
---
Getting Started
You'll need the Arduino IDE installed. The LiquidCrystal library comes with it by default so no extra installation needed.
Clone the repo and open `src/irrigation.ino` in Arduino IDE
Connect your Arduino Uno via USB
Select the right board and COM port under Tools
Upload
---
Author
Bennet Enifa Sagene
Hardware Engineering Student, University of Zimbabwe
bennetsagene@gmail.com
https://www.linkedin.com/in/bennet-sagene-76a096376
