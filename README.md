🚘 Autonomous Driverless Vehicle for Campus Navigation

(Path Following with Obstacle Detection + Real-Time Location Tracking)

This project demonstrates an autonomous driverless vehicle designed for campus navigation. It follows a predefined path using IR sensors, intelligently avoids obstacles with the help of an ultrasonic sensor, and provides safety alerts using a buzzer. The vehicle also stops and waits for students to board when all IR sensors detect a uniform surface (indicating an intersection or end of the path).

Additionally, the vehicle is equipped with a NodeMCU (ESP8266) and GPS module to track the real-time location of the vehicle. This data will be sent to Firebase via Wi-Fi, allowing for remote tracking. The mobile app integration is currently under development, and the vehicle's real-time location can be viewed on Firebase.

🔄 Note: The GPS system with NodeMCU is under development and may currently be experiencing some lag.
📱 App Development: The mobile app is still under development, but Firebase integration is working, and data is being fetched via Wi-Fi for tracking.
🚗 Features

Path Following: Follows a predefined path using three IR sensors.
Obstacle Detection: Avoids collisions using an ultrasonic sensor.
< 20 cm Obstacle: Vehicle stops + continuous buzzer alert.
20–40 cm Obstacle: Intermittent buzzer beeps.
> 40 cm: Normal operation, buzzer OFF.
Intersection Detection: Stops and waits when all IR sensors detect a uniform surface.
Motor Control: L298N motor driver controls two DC motors.
Real-Time Location Tracking: NodeMCU + GPS module fetches live GPS coordinates.
Firebase Integration (In Progress): Data is fetched via Wi-Fi from Firebase for location tracking.
App Integration (In Progress): A mobile app is being developed to display the vehicle’s live location on a map using GPS data (Currently in progress).
PID Control (In Progress): Smooth turning implementation using QTR-8RC sensor and PID algorithm is under development.
🛠️ Hardware Requirements

Arduino Uno (or compatible board)
NodeMCU (ESP8266)
GPS Module (Neo-6M or similar)
L298N Motor Driver
3 IR Sensors (for path detection)
Ultrasonic Sensor (HC-SR04)
Buzzer
2 DC Motors with Wheels
Robot Chassis
Jumper Wires and Power Supply
Breadboard or custom PCB (optional for neat integration)
QTR-8RC Line Sensor (for PID-based tracking, WIP)
Wi-Fi module for Firebase integration
🧠 Circuit Connections

Arduino Uno

Component	Arduino Pin
Left IR Sensor	A2
Center IR Sensor	A1
Right IR Sensor	A0
ENA (L298N)	10
IN1	5
IN2	4
IN3	3
IN4	2
ENB (L298N)	9
Ultrasonic Trig	6
Ultrasonic Echo	7
Buzzer	8
NodeMCU (ESP8266) + GPS Module

GPS Module Pin	NodeMCU Pin
VCC	3.3V
GND	GND
TX	D1 (GPIO5)
RX	D2 (GPIO4)
💡 Logic Summary

🛣️ Path Following
Based on IR sensor readings:

Center sensor detects path, sides do not → Move forward
Left sensor detects path → Turn right
Right sensor detects path → Turn left
All sensors detect or miss the path → Stop (Intersection or end of path)
🔧 PID-based line following with QTR-8RC is under development for more precise and smoother turns.
🚧 Obstacle Detection
< 20 cm → Stop and continuous buzzer
20–40 cm → Beep the buzzer
40 cm → Buzzer remains OFF
📡 Real-Time Location Tracking
NodeMCU reads live location from GPS module
GPS coordinates are sent via Wi-Fi to Firebase for tracking
App development is in progress to show live vehicle tracking on Google Maps
📄 Code

Main vehicle control logic is written in Arduino C (for the Uno).
GPS tracking logic is written using ESP8266-compatible code (TinyGPS++ + SoftwareSerial on NodeMCU).
Data from the GPS module is sent via Wi-Fi to Firebase for remote tracking.
The two microcontrollers run independently without the need for communication between them.
🔔 How to Use

Assemble all hardware as per the connections.
Upload the Arduino code to the Uno.
Upload GPS tracking code to NodeMCU.
Connect the NodeMCU to Wi-Fi and Firebase.
Place the robot on the predefined navigation path.
Power it on and observe:
It follows the path and avoids obstacles
It stops at intersections for boarding
It logs and sends real-time GPS data to Firebase for tracking
Note: The app integration is still in progress, but Firebase data can be accessed for vehicle location.
🚀 Further Improvements

PID Control for Smoother Navigation:
The PID algorithm will be implemented to fine-tune the steering, resulting in smoother turns and more accurate path following. The QTR-8RC sensor is currently being tested for this purpose.
App Integration:
The mobile app is still under development. Future versions will enable real-time GPS tracking on Google Maps, as well as user notifications when the vehicle is approaching a specific location or destination.
Enhanced Obstacle Avoidance:
The obstacle detection system can be improved by adding more ultrasonic sensors or other types of sensors (like LIDAR or infrared sensors) to detect obstacles from various angles, ensuring better safety and smoother operation.
👨‍💻 Author

Kishan Kumar
GitHub: @kishanP2005-ship-IT

