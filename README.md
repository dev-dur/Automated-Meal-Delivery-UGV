# Automated-Meal-Delivery-UGV
A 3-DOF PRP robotic manipulator for hospital meal automation.
Designed and integrated on a UGV to lift, rotate, and slide trays onto patient tables with precision.

## Project Info
- Year: 2024 – 2025
- Industry: Healthcare Robotics
- Client: University FYP (Final Year Project)
- Duration: 1 year

## 🧭 Concept

A 3-DOF PRP (Prismatic–Revolute–Prismatic) manipulator was engineered as the mechanical subsystem for an autonomous hospital meal delivery UGV.
- Degrees of Freedom: 3 (Lift, Rotate, Slide)
- Kinematic Chain: Open-chain
- Workspace: Funnel-shaped (optimized for patient table height & reach)

## Kinematic Modeling
### DH Parameters
| Joint | aᵢ | αᵢ   | dᵢ | θᵢ |
| ----- | -- | ---- | -- | -- |
| 1     | 0  | 0    | d₁ | 0  |
| 2     | a₂ | 0    | 0  | θ₂ |
| 3     | a₃ | -90° | d₃ | 0  |
- Forward Kinematics: Verified via chained transformation matrices; theoretical vs actual trajectories matched.
- Inverse Kinematics: Derived equations to compute distance for reaching target points in space.
<img width="1080" height="607" alt="image" src="https://github.com/user-attachments/assets/2abcf1b5-37b5-4d65-b2d3-7c56201f2fc4" />


## Mechanical Subsystems
### 1. Lifter – Pulley-Based Lift System
- Component: 3D-printed PLA lifting platform
- Mechanism: Aluminum pulley (21-T5-24), ratio 1:1
- Motor: NEMA 23 stepper (5–61 Nm torque)
- Performance: ~160 g payload, ~20 mNm torque requirement
- 3D Rationale: Lightweight, tray-specific geometry

### 2. Rotator – Spur Gear Turntable
- Gears: 3D-printed PETG double helical gears (20T driving, 24T mating, ratio 1:1.2)
- Motor: Servo motor (180°, ~1.08 Nm torque)
- 3D Rationale: Smoother meshing, lower vibration, tighter tolerances

### 3. Slider – Rack & Pinion Horizontal Drive
- Rack: 150 mm PETG
- Pinion: PETG gear matched to rack
- Motor: N20 DC motor (~0.1–0.4 Nm torque)
- Payload: ~163 g
- 3D Rationale: Modular design, easy repair, sufficient rigidity

## Material Transition Justification
| Component        | Old Method      | 3D Printed Alternative | Reason for Shift                              |
| ---------------- | --------------- | ---------------------- | --------------------------------------------- |
| Belt Clamps      | Metal welding   | PETG                   | Easier fabrication, flexible, crack-resistant |
| Spur Gears       | Laser-cut metal | PETG (Double Helical)  | Smoother torque transfer, reduced backlash    |
| Lifting Platform | Sheet metal     | PLA                    | Tray-fitting geometry, reduced actuator load  |
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9dc3636a-68df-4d0c-ae2b-12535db339aa" />


## Motor Control System
| Motion  | Actuator        | Control Method               | Travel Logic                    |
| ------- | --------------- | ---------------------------- | ------------------------------- |
| Lifter  | NEMA 23 Stepper | ESP32 + Arduino (UART)       | Step-based linear interpolation |
| Rotator | Servo Motor     | ESP32 (PWM control)          | Fixed angular positions         |
| Slider  | N20 DC Motor    | ESP32 (timed on/off control) | Time-bound linear actuation     |

## Structural & Modal Analysis (FEA)
| Component          | Max Stress (MPa) | Max Deformation (mm) | Observations                        |
| ------------------ | ---------------- | -------------------- | ----------------------------------- |
| Belt Clamp (PETG)  | 2.85             | Low                  | Good static distribution            |
| Lifted Platform    | 3.06             | Peak under dynamic   | Verified with transient simulation  |
| Spur Gear (x-axis) | 0.00175          | Negligible           | Stable gear meshing                 |
| Shaft (Metal)      | 6.6              | Acceptable           | Modal vibration observed at ~354 Hz |
<img width="1080" height="823" alt="image" src="https://github.com/user-attachments/assets/c6a73c06-ca60-41cc-bcd8-026ed711d046" />


## Conclusion
This mechanical subsystem achieves:
- Fully functional 3-DOF robotic actuation
- Optimized 3D-printed parts for cost, weight, and adaptability
- Modular & serviceable design, tailored for hygienic hospital use
- Integration of robot kinematics, CAD, FEA, and control systems under real-world healthcare constraints
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/d78fa4f6-ca6c-4161-8ca3-52b08c66b089" />

