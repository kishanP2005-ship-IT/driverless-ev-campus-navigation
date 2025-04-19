# 🚘 Autonomous Driverless Vehicle for Campus Navigation  
### *(Path Following with Obstacle Detection + Real-Time Location Tracking)*

This project demonstrates an autonomous driverless vehicle designed for campus navigation. It follows a predefined path using IR sensors, intelligently avoids obstacles with the help of an ultrasonic sensor, and provides safety alerts using a buzzer. The vehicle also stops and waits for students to board when all IR sensors detect a uniform surface (indicating an intersection or end of the path).

Additionally, the vehicle is equipped with a NodeMCU (ESP8266) and GPS module to track its real-time location. The GPS data is sent to Firebase via Wi-Fi, and app integration is currently under development for map-based live location tracking.

> 🔄 **Note:** The GPS system with NodeMCU is active but may experience slight delays.  
> 📱 **App Status:** Mobile app is under development. GPS data is currently sent to Firebase and can be accessed there.

---

## 🚗 Features

- **Path Following:** Follows a predefined path using three IR sensors.  
- **Obstacle Detection:** Avoids collisions using an ultrasonic sensor.  
- **< 20 cm Obstacle:** Vehicle stops and buzzer sounds continuously.  
- **20–40 cm Obstacle:** Intermittent buzzer beeps.  
- **> 40 cm Obstacle:** Buzzer remains OFF.  
- **Intersection Detection:** Stops and waits when all IR sensors detect a uniform surface.  
- **Motor Control:** L298N motor driver controls two DC motors.  
- **Real-Time Location Tracking:** NodeMCU + GPS module fetches live coordinates.  
- **Firebase Integration:** Sends data to Firebase via Wi-Fi.  
- **App Integration (In Progress):** Under development to display vehicle’s live location on a map.  
- **PID Control (Coming Soon):** For smoother and more accurate turning using QTR-8RC sensors.

---

## 🛠️ Hardware Requirements

- Arduino Uno (or compatible board)  
- NodeMCU (ESP8266)  
- GPS Module (Neo-6M or similar)  
- L298N Motor Driver  
- 3 IR Sensors (for path detection)  
- Ultrasonic Sensor (HC-SR04)  
- Buzzer  
- 2 DC Motors with Wheels  
- Robot Chassis  
- Jumper Wires and Power Supply  
- Breadboard or Custom PCB (for integration)  
- QTR-8RC Sensor (for future PID integration)

---

## 🧠 Circuit Connections

### Arduino Uno

| Component          | Arduino Pin |
|--------------------|-------------|
| Left IR Sensor     | A2          |
| Center IR Sensor   | A1          |
| Right IR Sensor    | A0          |
| ENA (L298N)        | 10          |
| IN1                | 5           |
| IN2                | 4           |
| IN3                | 3           |
| IN4                | 2           |
| ENB (L298N)        | 9           |
| Ultrasonic Trig    | 6           |
| Ultrasonic Echo    | 7           |
| Buzzer             | 8           |

### NodeMCU (ESP8266) + GPS Module

| GPS Module Pin | NodeMCU Pin |
|----------------|-------------|
| VCC            | 3.3V        |
| GND            | GND         |
| TX             | D1 (GPIO5)  |
| RX             | D2 (GPIO4)  |

---

## 💡 Logic Summary

### 🛣️ Path Following

Based on IR sensor readings:

- **Center sensor detects path, sides do not:** Move forward  
- **Left sensor detects path:** Turn right  
- **Right sensor detects path:** Turn left  
- **All sensors detect or miss the path:** Stop (intersection/end of path for boarding)

> 🔧 *PID-based navigation using QTR-8RC is in progress for more accurate control.*

### 🚧 Obstacle Detection

- **< 20 cm:** Stop and continuous buzzer  
- **20–40 cm:** Intermittent beep  
- **> 40 cm:** No alert, continue path

### 📡 Real-Time Location Tracking

- NodeMCU reads coordinates from GPS module  
- Sends data via Wi-Fi to Firebase  
- Mobile app (in development) will display data on Google Maps

---

## 📄 Code Overview

- **Arduino Uno:** Handles path following, obstacle detection, and motor control using IR & ultrasonic sensors.  
- **NodeMCU:** Handles GPS tracking and Wi-Fi communication with Firebase.  
- **Independent Operation:** Arduino and NodeMCU run independently without needing to communicate via serial.

---

## 🔔 How to Use

1. Assemble hardware as per connections above.  
2. Upload Arduino sketch to Uno (for navigation).  
3. Upload GPS tracking sketch to NodeMCU (Firebase + TinyGPS++).  
4. Connect NodeMCU to Wi-Fi and Firebase.  
5. Place robot on the predefined path.  
6. Power the robot and observe:
   - Path tracking and obstacle avoidance  
   - Stopping at intersections  
   - GPS data logged and sent to Firebase  

---

## 🚀 Further Improvements

- **PID Control:** Under development using QTR-8RC sensors for smoother line tracking and precise turns.  
- **Mobile App Integration:** Being built to fetch Firebase GPS data and display real-time vehicle location on Google Maps.  
- **Advanced Obstacle Avoidance:** Planned with additional ultrasonic/LIDAR sensors for 360° safety.

---

## 👨‍💻 Author

**Kishan Kumar**  
📧 Email: [kishankumarrap@gmail.com](mailto:kishankumarrap@gmail.com)  
🔗 GitHub: [@kishanP2005-ship-IT](https://github.com/kishanP2005-ship-IT)






