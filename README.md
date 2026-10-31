# Motor Overheat Alert System

A low-cost embedded system that monitors motor temperature in real time using an **Arduino Uno** and an **LM35 temperature sensor**, and warns the user with a three-level LED indicator and a buzzer alert when the motor overheats.

Developed as an internship project in embedded systems and IoT.

---

## Overview

Motors can be damaged or become a safety hazard when they run too hot. This project continuously reads the motor's temperature and shows its state at a glance, then triggers an audible alarm as soon as a preset threshold is crossed.

## Features

- Real-time temperature monitoring with the LM35 sensor
- Three-level status indication:
  - **Green LED**: Normal
  - **Yellow LED**: Warning
  - **Red LED**: Overheat
- Buzzer turns on automatically when the temperature exceeds the preset threshold
- Low-cost and simple to build with common components
- Tested under different temperature conditions with reliable real-time response

## Components Used

| Component | Purpose |
|-----------|---------|
| Arduino Uno | Main microcontroller |
| LM35 temperature sensor | Measures motor temperature |
| LEDs (Green, Yellow, Red) | Normal / Warning / Overheat indication |
| Buzzer | Audible overheat alert |
| Resistors (220 Ω for LEDs) and jumper wires | Circuit connections |
| Breadboard | Prototype assembly |

## Software and Tools

- Arduino IDE (programming and debugging)
- Proteus (circuit simulation)

## How It Works

1. The LM35 outputs an analog voltage proportional to temperature (10 mV per °C).
2. The Arduino reads this value through an analog input pin and converts it to degrees Celsius.
3. The temperature is compared against the preset thresholds:
   - Below the warning threshold: **Green LED** on
   - Between the warning and overheat thresholds: **Yellow LED** on
   - Above the overheat threshold: **Red LED** on and **buzzer** activated

| State | Temperature range | Indicator |
|-------|-------------------|-----------|
| Normal | below 40 °C | Green LED |
| Warning | 40 °C to 60 °C | Yellow LED |
| Overheat | above 60 °C | Red LED + Buzzer |

The thresholds can be changed in the code to suit different motors.

## Circuit Connections

| Component | Arduino Pin |
|-----------|-------------|
| LM35 (output) | A0 |
| Green LED | D2 |
| Yellow LED | D3 |
| Red LED | D4 |
| Buzzer | D5 |

LM35 power pin goes to 5V and its ground pin goes to GND. Each LED connects through a 220 Ω resistor to GND.

![Circuit diagram](images/circuit.png)

## Getting Started

1. Clone this repository:
   ```
   git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
   ```
2. Open the `.ino` file in the **Arduino IDE**.
3. Assemble the circuit as shown in the connection table above.
4. Select **Board: Arduino Uno** and the correct COM port.
5. Upload the sketch and (optionally) open the Serial Monitor to view temperature readings.

## Project Structure

```
├── motor_overheat_alert.ino   # Arduino sketch
├── images/                    # Circuit diagram, photos, screenshots
└── README.md
```

## Results

- The LM35 monitored temperature accurately.
- The system correctly switched between Normal, Warning and Overheat states.
- The buzzer activated immediately when the threshold was exceeded.
- The prototype responded reliably in real time across different temperature conditions.

![Working prototype](images/prototype.jpg)

## Future Improvements

- Add an LCD display to show the live temperature value
- Send alerts to a phone using an ESP32 and the Blynk IoT platform
- Automatically cut off motor power when the Overheat state is reached
- Log temperature data for analysis

## What I Learned

- Interfacing analog sensors with a microcontroller
- Real-time data acquisition and threshold-based control
- Circuit assembly, testing and debugging
- Hardware and software integration using the Arduino IDE
