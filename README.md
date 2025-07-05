# 🛸 Autonomous Parrot Minidrone System | Competition Deployment

> A full-stack autonomous control system for the **Parrot Mambo Minidrone**, integrating flight stabilization, autonomous waypoint navigation, and obstacle-aware trajectory tracking using MATLAB and Simulink.

---

## 🎯 Project Objective

Design an embedded flight control and autonomy stack enabling the **Parrot Minidrone** to:
- Perform autonomous takeoff, waypoint following, and precise landing.
- Navigate a pre-mapped course with obstacle avoidance and error correction.
- Operate in a fully embedded setup, running real-time on the drone.

---

## 🛠️ Technologies & Tools

| Domain                    | Tools / Libraries                                              |
|----------------------------|---------------------------------------------------------------|
| Control System Design      | MATLAB, Simulink, Stateflow                                   |
| Embedded Deployment        | Simulink Support Package for Parrot Minidrone, Embedded C     |
| Flight Control             | PID controllers, Finite State Machines (FSM)                  |
| Path Planning              | Cubic spline interpolation, Discrete waypoint generation      |
| Communication              | BLE (Bluetooth Low Energy)                                    |
| Sensors                    | IMU (gyro + accelerometer), Ultrasonic altimeter, Camera     |
| Simulation & Testing       | MATLAB virtual drone simulator, Onboard closed-loop testing   |

---

## ⚙️ System Architecture

### ➤ Embedded Flight Control System
- Developed discrete **PID controllers** for pitch, roll, yaw, and altitude, each running at ~50 Hz.
- Stabilized body frame errors using sensor fusion data from the drone's onboard IMU.
- Implemented **anti-windup compensation** in integral terms to prevent control saturation.

### ➤ Finite State Machine (FSM) for Mission Execution
- Mission stages included:
  - Idle → Takeoff → Waypoint Traverse → Obstacle Avoidance → Hover → Landing.
- State transitions were triggered by sensor thresholds (altitude, position error) and mission progress flags.

### ➤ Autonomous Waypoint Navigation
- Waypoints defined as relative X-Y-Z coordinates.
- Used **cubic spline interpolation** for smooth trajectory generation.
- Applied feedforward velocity planning combined with closed-loop positional corrections.

### ➤ Obstacle Detection & Avoidance (Simulated)
- Modeled virtual obstacles in MATLAB simulation.
- Implemented simple reactive avoidance (heading and altitude shift) when obstacle zones were detected.

### ➤ Embedded Deployment
- Converted the Simulink model to optimized C code using Embedded Coder.
- Deployed via **MATLAB Simulink Support Package** directly onto the Parrot Minidrone.
- Real-time data logging enabled via BLE telemetry.

---

## 🔬 Key Technical Features

- **Multi-Axis PID Stabilization:** Individual tuning of pitch, roll, yaw, and thrust loops with dynamic setpoints.
- **Waypoint Navigation:** Error-correcting navigation towards sequential waypoints, minimizing overshoot.
- **Altitude Control:** Ultrasonic-based altitude feedback maintaining ±5 cm deviation.
- **Sensor Fusion:** Combined accelerometer and gyroscope data for orientation estimation.
- **Trajectory Smoothing:** Reduced jerky movements during path transitions using cubic splines.

---

## 🧪 Testing & Validation

### Simulation
- Simulated complete mission flow using MATLAB's virtual Minidrone environment.
- Verified stability during sharp turns and altitude changes.


---

## 📈 Future Improvements

- Vision-based obstacle detection using the onboard FPV camera and OpenCV for dynamic avoidance.
- Optimize trajectory planning for smoother curved paths using Bézier or B-spline curves.
- Implement SLAM or EKF-based localization for better positional accuracy.
- Offload compute-heavy tasks to an external companion computer (e.g., Raspberry Pi Zero W) if needed.
- Extend to outdoor flights using GPS data fusion.

---

