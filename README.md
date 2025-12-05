# 🐜 Hexapod Tripod Gait (Arduino)

A bio-inspired six-legged (hexapod) robot designed to mimic ant locomotion using a simple, stable **tripod gait**.  
This project demonstrates efficient walking using only **6 servos** (1 DOF per leg) and **passive mechanical knees** with forward stops.

---

## ⚙️ Overview

- **Controller:** Arduino Uno  
- **Servos:** 6 × Hitec HS-425BB  
- **Material:** 1/4″ MDF body and legs  
- **Degrees of Freedom:** 1 per leg (hip rotation only)  
- **Knee Joints:** Passive with mechanical stops (~±7.5°)  
- **Walking Modes:** Forward and backward (automatic direction reversal supported)  
- **Gait:** Tripod gait for smooth, stable locomotion  
- **Power:** 6 V battery pack (low & centered for stability)
- **Speed:** 1.3 body lengths/s (0.24 m/s)

---

## 🦿 Motion Summary

| Feature | Description |
|----------|-------------|
| **Tripod A** | Left Front (LF), Right Middle (RM), Left Rear (LR) |
| **Tripod B** | Right Front (RF), Left Middle (LM), Right Rear (RR) |
| **Swing Phase** | Tripod lifts and moves forward relative to body |
| **Stance Phase** | Opposite tripod pushes body forward |
| **Smooth Interpolation** | Servos move in small increments for natural motion |
| **Forward/Backward Walking** | Controlled by sign of motion direction |

---

## 🔩 Mechanical Design

- Upper leg length: ~60 mm  
- Lower leg length: ~50 mm  
- Legs offset 26 mm from body centerline  
- Mechanical stops limit knee motion:
  - **Forward Stop:** ~7.5° forward of vertical 
- Elastic assist to lift lower leg during swing  
- Rubber feet with rounded toe to prevent catching  

---

## 🧰 Electronics & Connections

| Component | Connection |
|------------|-------------|
| Servos | Pins 2–7 (LF→RR order) |
| Power | 6 V Li-ion/NiMH battery |
| Ground | Common ground for Arduino + servos |
| Optional | IR sensor for direction reversal trigger |

**Servo Pin Assignments:**
| Servo | Pin |
|-------|-----|
| LF | 2 |
| LM | 3 |
| LR | 4 |
| RF | 5 |
| RM | 6 |
| RR | 7 |

---

## 💻 Code Summary

**Language:** Arduino C++  
**Libraries:**  
- `Servo.h`

**Main features:**
- Tripod gait control  
- Smooth motion interpolation  
- Direction toggle for forward/backward walking  
- Adjustable step duration and stride length  

### Key Parameters
| Variable | Description | Default |
|-----------|-------------|----------|
| `swingMax` | Max forward swing angle | 20° |
| `swingMin` | Max backward swing angle | -20° |
| `stepDelay` | Time per half-step | 800 ms |
| `smoothSteps` | Steps for interpolation | 20 |
| `direction` | 1 = forward |

---

## 🔧 Fabrication Checklist

1. Cut body and legs from MDF; drill servo holes and spacers.  
2. Add mechanical knee stops at ±7.5°; make adjustable.  
3. Mount 6 servos with shoulder screws (no glue).  
4. Install electronics low and centered.  
5. Wire all servos to Arduino (pins 2–7).  
6. Calibrate all servos to 90° neutral before attaching horns.  
7. Run `hexapod_tripod_gait.ino` and test each leg individually.  

---

## 🧪 Testing Procedure

1. **Single Leg Test:** Sweep one servo slowly and confirm stops engage correctly.  
2. **Tripod Dry Run:** Test small amplitude (±10°) to verify gait timing.  
3. **Forward Walk:** Walk forward 5 m, fine-tune step size if dragging occurs.
5. **Full Test:** Run 5 m forward + 5 m backward with tuned stride. 
