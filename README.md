# 🌱 Automatic Plant Watering System

An Arduino-based smart irrigation system that continuously monitors soil moisture and automatically waters plants when the soil becomes too dry. Designed for both indoor and outdoor plants, it conserves water while keeping plants healthy with no manual effort.

> **Project by:** Astha Wanwey, Kinjal Bhartiya & Saloni Lihare
> **Department:** Electronics and Telecommunication Engineering
> **Institute:** G.H. Raisoni College of Engineering, Nagpur

---

## 📖 Table of Contents

- [Introduction](#-introduction)
- [Features](#-features)
- [Components Required](#-components-required)
- [How It Works](#-how-it-works)
- [Circuit Connections](#-circuit-connections)
- [Installation & Setup](#-installation--setup)
- [Sample Code](#-sample-code)
- [Advantages](#-advantages)
- [Future Scope](#-future-scope)
- [Conclusion](#-conclusion)
- [Team](#-team)
- [License](#-license)

---

## 📌 Introduction

In an era where technology intertwines with agriculture, automatic plant watering systems have emerged as a vital solution to meet the growing demand for efficient irrigation. These systems cater to both indoor and outdoor plants, ensuring they receive the appropriate amount of water based on their specific needs.

This technology not only conserves water but also supports sustainable gardening practices, making it invaluable for hobbyists and commercial growers alike.

---

## ✨ Features

- 💧 Real-time soil moisture monitoring
- 🤖 Automatic pump control based on a moisture threshold
- 📟 Live moisture status displayed on a 16x2 LCD
- 🌡️ Optional temperature and humidity sensing (DHT sensor)
- 🔋 Low-power, USB-powered operation
- 🔧 Easy to build, customize, and expand

---

## 🧰 Components Required

| No. | Component | Purpose |
|-----|-----------|---------|
| 1 | Arduino (Uno/Nano) microcontroller | Brain of the system |
| 2 | Soil moisture sensor | Measures soil moisture level |
| 3 | Small submersible water pump | Delivers water to the plant |
| 4 | Relay module / motor driver | Switches the pump on and off |
| 5 | 16x2 LCD display (with I2C) | Displays moisture status |
| 6 | DHT11 temperature & humidity sensor *(optional)* | Environmental data |
| 7 | Power supply | Powers the circuit |
| 8 | Jumper wires | Connections |
| 9 | USB power line | Power and programming |

---

## ⚙️ How It Works

1. The **soil moisture sensor** continuously measures the moisture level of the soil.
2. The sensor sends this data to the **microcontroller**.
3. When the moisture drops **below a predetermined threshold**, the microcontroller activates the **water pump** through the relay.
4. The pump delivers water to the plant until the soil reaches the desired moisture level.
5. The pump switches off automatically, and the system keeps monitoring.

The system can also be programmed to water at specific times or in response to weather forecasts, further improving efficiency.

```
 ┌──────────────┐     ┌───────────────┐     ┌────────────┐
 │ Soil Moisture│────▶│  Arduino      │────▶│ Relay      │───▶ Water Pump
 │ Sensor       │     │  (Controller) │     │ Module     │
 └──────────────┘     └───────┬───────┘     └────────────┘
                              │
                              ▼
                        16x2 LCD Display
```

---

## 🔌 Circuit Connections

> Adjust pin numbers to match your wiring.

| Component | Arduino Pin |
|-----------|-------------|
| Soil moisture sensor (AO) | A0 |
| Relay module (IN) | D7 |
| DHT11 (DATA) | D2 |
| LCD (SDA / SCL) | A4 / A5 |
| All VCC / GND | 5V / GND |

---

## 🚀 Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/automatic-plant-watering-system.git
   cd automatic-plant-watering-system
   ```
2. **Install the Arduino IDE** from [arduino.cc](https://www.arduino.cc/en/software).
3. **Install required libraries** (Sketch → Include Library → Manage Libraries):
   - `LiquidCrystal I2C`
   - `DHT sensor library` *(if using DHT11)*
4. **Assemble the circuit** following the connection table above.
5. **Open** the `.ino` file, select your board and port, and click **Upload**.
6. **Calibrate** the threshold value for your soil and sensor.

---

## 💻 Sample Code

```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

#define SOIL_PIN   A0
#define RELAY_PIN  7
#define THRESHOLD  500   // Higher value = drier soil; calibrate for your sensor

LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  pinMode(RELAY_PIN, OUTPUT);
  digitalWrite(RELAY_PIN, HIGH);   // Pump OFF (active-low relay)
  lcd.init();
  lcd.backlight();
  lcd.print("Plant Watering");
  delay(2000);
  lcd.clear();
}

void loop() {
  int moisture = analogRead(SOIL_PIN);

  lcd.setCursor(0, 0);
  lcd.print("Moisture: ");
  lcd.print(moisture);
  lcd.print("   ");

  if (moisture > THRESHOLD) {
    digitalWrite(RELAY_PIN, LOW);  // Pump ON
    lcd.setCursor(0, 1);
    lcd.print("Pump: ON         ");
  } else {
    digitalWrite(RELAY_PIN, HIGH); // Pump OFF
    lcd.setCursor(0, 1);
    lcd.print("Pump: OFF        ");
  }

  delay(1000);
}
```

> ⚠️ Replace this sample with your actual project code before publishing.

---

## 🏆 Advantages

1. **Water conservation**: waters only when needed
2. **Time saving**: no manual watering required
3. **Healthier plants**: consistent, optimal moisture levels
4. **Remote monitoring**: can be extended with IoT modules
5. **Customization**: thresholds and schedules are easy to adjust

---

## 🔭 Future Scope

- Wi-Fi / IoT integration (ESP8266, ESP32) for mobile app control
- Weather-forecast-based watering
- Multiple plant zones with multiple sensors
- Solar-powered operation
- Data logging and analytics dashboard

---

## ✅ Conclusion

The automatic plant watering system represents a significant advancement in agricultural technology, providing a sustainable solution to water management. By automating the watering process, it ensures that plants receive the right amount of water, thereby promoting growth and health while conserving resources.

---

## 👩‍💻 Team

| Name | Role |
|------|------|
| Astha Wanwey | Developer |
| Kinjal Bhartiya | Developer |
| Saloni Lihare | Developer |

**Guided by / Institution:** Department of Electronics and Telecommunication Engineering, G.H. Raisoni College of Engineering, Nagpur

---

## 📸 Project Images

Add your project photos to an `images/` folder and reference them here:

```markdown
![Project Setup](images/project.jpg)
```

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

⭐ If you found this project useful, consider giving it a star!
