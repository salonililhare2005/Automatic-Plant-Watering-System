# 🌱 Automatic Plant Watering System

An embedded-systems project that monitors soil moisture and waters plants automatically, so they get the right amount of water without manual effort.

> **Developed by:** Astha Wanwey, Kinjal Bhartiya & Saloni Lihare
> **Department:** Electronics and Telecommunication Engineering (UG)
> **Institute:** G.H. Raisoni College of Engineering, Nagpur

![Project Prototype](images/project-prototype.jpg)

---

## 📖 Introduction

As technology and agriculture increasingly overlap, automatic plant watering systems have become a practical answer to the demand for efficient irrigation. They suit both indoor and outdoor plants and deliver water according to each plant's actual needs. The system conserves water and supports sustainable gardening, making it useful for hobbyists and commercial growers alike.

---

## ✨ Features

- Continuous, real-time soil moisture monitoring
- Automatic pump activation when moisture falls below a set threshold
- Live status shown on an LCD display
- Low-cost, compact and easy to build
- Can be extended with scheduling, weather-based watering and remote monitoring

---

## 🧰 Components Used

| No. | Component | Purpose |
|-----|-----------|---------|
| 1 | Sensors | Sense environmental conditions |
| 2 | Microcontroller | Reads sensor data and controls the pump |
| 3 | Water pump | Delivers water to the plant |
| 4 | Power supply | Powers the circuit |
| 5 | Soil moisture sensor | Measures moisture level in the soil |
| 6 | Jumper wires | Circuit connections |
| 7 | Small submersible pump | Draws water from the reservoir |
| 8 | USB power line | Supplies power to the board |

---

## ⚙️ How It Works

1. The **soil moisture sensor** continuously measures moisture in the soil.
2. It sends the readings to the **microcontroller**.
3. If the moisture drops **below the predetermined threshold**, the microcontroller switches the **water pump ON**.
4. Water reaches the plant through the chosen watering mechanism.
5. Sensor feedback allows real-time adjustment, and the pump turns **OFF** once the soil is moist enough.
6. Some setups can also be programmed to water at specific times or in response to weather forecasts.

```
 Soil Moisture Sensor ──► Microcontroller ──► Relay / Driver ──► Water Pump ──► Plant
                               │
                               └──► LCD Display (status)
```

---

## 🔌 Circuit Diagram

![Circuit Diagram](images/circuit-diagram.png)

> Add your circuit diagram or wiring photo at `images/circuit-diagram.png`.

---

## 🚀 Getting Started

### Prerequisites
- Arduino IDE (or the IDE for your microcontroller)
- The hardware listed above
- USB cable

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/automatic-plant-watering-system.git
cd automatic-plant-watering-system
```

1. Assemble the circuit as shown in the circuit diagram.
2. Open the code file from the `src/` folder in the Arduino IDE.
3. Select your board and COM port.
4. Upload the code.
5. Place the moisture sensor in the soil and the pump in the water reservoir.

### Example Logic (adjust pins and threshold for your setup)

```cpp
const int sensorPin = A0;   // soil moisture sensor
const int pumpPin   = 8;    // pump / relay control
const int threshold = 500;  // calibrate for your sensor and soil

void setup() {
  pinMode(pumpPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int moisture = analogRead(sensorPin);
  Serial.println(moisture);

  // Most sensors read higher when the soil is dry; verify yours.
  if (moisture > threshold) {
    digitalWrite(pumpPin, HIGH);  // soil dry -> pump ON
  } else {
    digitalWrite(pumpPin, LOW);   // soil moist -> pump OFF
  }
  delay(1000);
}
```

---

## ✅ Advantages

- 💧 **Water conservation**: waters only when needed
- ⏱️ **Time saving**: no manual watering
- 🌿 **Healthier plants**: consistent moisture levels
- 📡 **Remote monitoring**: can be extended with IoT modules
- 🎛️ **Customization**: thresholds and schedules can be tuned per plant

---

## 🔮 Future Scope

- IoT / mobile app monitoring (Wi-Fi or GSM)
- Weather-forecast-based watering
- Multiple plant zones with multiple sensors
- Solar-powered operation
- Water-level detection in the reservoir

---

## 📁 Project Structure

```
automatic-plant-watering-system/
├── images/
│   ├── project-prototype.jpg
│   └── circuit-diagram.png
├── src/
│   └── plant_watering.ino
├── docs/
│   └── project-poster.pptx
└── README.md
```

---

## 🏁 Conclusion

The automatic plant watering system is a meaningful step forward in agricultural technology and a sustainable approach to water management. By automating watering, it ensures plants receive the right amount of water, promoting growth and health while conserving resources.

---

## 👩‍💻 Team

| Name | Department |
|------|------------|
| Astha Wanwey | Electronics & Telecommunication Engg. |
| Kinjal Bhartiya | Electronics & Telecommunication Engg. |
| Saloni Lihare | Electronics & Telecommunication Engg. |

G.H. Raisoni College of Engineering, Nagpur

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
