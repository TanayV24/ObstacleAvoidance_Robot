<div align="center">

# 🤖 Obstacle Avoidance Robot

### Autonomous Robot for Environment Navigation & Obstacle Detection-Avoidance


**A DIY autonomous wheeled robot capable of detecting obstacles (using ultrasonic / proximity sensors) and dynamically avoiding them — ideal for robotics learning, projects or practical demonstrations.**

[🐛 Report Bug](https://github.com/TanayV24/ObstacleAvoidance_Robot/issues) | [💡 Request Feature](https://github.com/TanayV24/ObstacleAvoidance_Robot/issues)

</div>

---

## ✨ Features

### 🛞 Core Robot Capabilities
- 🔊 **Real-time Obstacle Detection** using sensor(s) — ultrasonic or proximity  
- 🔄 **Autonomous Navigation Logic** — continuous forward movement; on obstacle detection, execute avoidance manoeuvres (stop, reverse/turn, continue) :contentReference[oaicite:1]{index=1}  
- 🧭 **Dynamic Path Adjustment** — basic reactive behaviour without pre-mapped environment :contentReference[oaicite:2]{index=2}  
- ⚙️ **Configurable Sensor Thresholds** — define safe distance for obstacle detection  
- 🔋 **Lightweight & Embedded-Ready** — runs on microcontroller / Arduino / HC-SR04 sensor + motor driver modules :contentReference[oaicite:3]{index=3}  

### 🔧 Hardware & Software Integration
- 🛠 **Motor control via driver module (e.g. L298N or similar)**  
- 📡 **Ultrasonic / proximity sensor integration** for environment awareness  
- 📄 **Modular and readable code** (embedded C / Arduino sketch or Python if using SBC)  
- 🔄 **Simple to extend** — you can add line-following, remote-control, or map-based navigation later  

---

## 🛠 Tech Stack / Hardware Stack

| Layer | Components / Technologies |
|-------|---------------------------|
| Microcontroller | Arduino UNO / ATmega / any MCU |
| Sensors | HC-SR04 Ultrasonic Sensor (or other proximity sensors) |
| Motor Driver | L298N / H-Bridge driver + DC motors / wheels / chassis |
| Power Supply | Battery pack suitable for motors & MCU |
| Embedded Code | C / C++ (Arduino IDE) or Microcontroller-compatible code |
| Optional | Additional sensors (IR, line sensors), actuators |

---

## 📋 Prerequisites & Hardware Requirements

| Component | Notes |
|----------|--------|
| Microcontroller (Arduino UNO or similar) | Must support digital I/O + compatible with motor driver |
| Ultrasonic or Proximity Sensor (e.g. HC-SR04) | For obstacle detection |
| Motor Driver Module (e.g. L298N) | To drive DC motors / wheels |
| Wheels + Chassis + Power Supply | Basic robot frame + battery for motors + MCU |
| Jumper Wires / Connectors / Breadboard (optional) | For prototyping wiring |

---

## ⚙️ Installation & Setup / Build Instructions

### 1. Clone the project
```bash
git clone https://github.com/TanayV24/ObstacleAvoidance_Robot.git
cd ObstacleAvoidance_Robot
````

### 2. (If using Arduino) Open the sketch / code file

* Load into Arduino IDE
* Connect your HC-SR04 sensor, motor driver, motors and battery as per wiring diagram

### 3. Upload to Microcontroller

* Select correct board and port
* Upload
* Power motors via battery (not via USB, for safety)

### 4. Place robot on ground / test surface

* On power-on, robot moves forward until obstacle detected
* At safe-distance threshold, robot executes avoidance behaviour (stop + turn / reverse + forward)

```

**Description of key parts:**

* `hardware/`: Contains wiring diagrams, component lists, and hardware setup instructions — helps anyone rebuild the robot physically.
* `firmware/`: The core embedded code that runs on microcontroller — includes the main logic (sensor reading, obstacle detection, motor control), configuration, and modular structure for maintainability.
* `docs/`: Documentation for how to build, test, calibrate sensors, and use the robot safely.
* `simulations/`: (Optional) If you provide a software simulation or virtual test version (e.g. Python + sensors mock / ROS), helpful for testing before deploying on hardware.

---

## 🐛 Troubleshooting & Common Issues

<details>
<summary>Robot doesn’t move or motors don’t spin</summary>

* Check motor driver wiring & power supply (battery).
* Ensure EN / enable pins on driver are set correctly (if using L298N).
* Disconnect sensors before testing motor power — sensor noise may interfere.

</details>

<details>
<summary>Obstacle detection fails / robot collides into obstacle</summary>

* Verify sensor wiring (power, trig, echo).
* Calibrate distance threshold — ensure HC-SR04 echo distance matches obstacle distance.
* Avoid reflective or small obstacles; sensor may misread.
* Add short delay after sensor reading to avoid noisy spikes.

</details>

<details>
<summary>Robot gets stuck in loop or behaves unstable</summary>

* Add random turn angle instead of fixed 180°, to avoid bouncing back into same obstacle. This is common strategy in obstacle avoidance logic. ([introtoroboticsv2.readthedocs.io][1])

</details>


[1]: https://introtoroboticsv2.readthedocs.io/en/latest/course/measuring_distance/obstacle_avoidance.html?utm_source=chatgpt.com "Obstacle Avoidance — XRP 2023.0 documentation"
