# CAN ID Map

This document defines the official Lighting Robotics CAN ID assignments for all devices on the robot.

## 🔒 Rules for CAN IDs

1. CAN IDs must NEVER be changed without updating this document.
2. Every device must have a unique CAN ID.
3. CAN IDs are grouped by subsystem.
4. Subsystem ranges are reserved (see table below).
5. Changes require:
   - Updating this document
   - Updating Constants.java
   - Verifying in REV Hardware Client

---

## 📊 CAN ID Allocation Strategy

| Range | Subsystem                    |
| ----- | ---------------------------- |
| 0     | RoboRIO                      |
| 1–9   | Drivetrain                   |
| 10–19 | Intake                       |
| 20–29 | Shooter                      |
| 30–39 | Climber                      |
| 40–49 | Arm / Pivot                  |
| 50–59 | Sensors                      |
| 60–62 | Power Distribution / Control |
| 63    | Reserved (Do Not Use)        |

---

# 🚗 Drivetrain

| Device                  | CAN ID | Controller Type | Notes                |
| ----------------------- | ------ | --------------- | -------------------- |
| Front Left Drive Motor  | 1      | SparkMax        | NEO                  |
| Front Right Drive Motor | 2      | SparkMax        | NEO                  |
| Back Left Drive Motor   | 3      | SparkMax        | NEO                  |
| Back Right Drive Motor  | 4      | SparkMax        | NEO                  |
| Pigeon Gyro             | 5      | CTRE            | Mounted on belly pan |

---

# 🟢 Intake

| Device        | CAN ID | Controller Type | Notes            |
| ------------- | ------ | --------------- | ---------------- |
| Intake Roller | 10     | SparkMax        | NEO 550          |
| Intake Pivot  | 11     | SparkMax        | Absolute encoder |

---

# 🔴 Shooter

| Device        | CAN ID | Controller Type | Notes    |
| ------------- | ------ | --------------- | -------- |
| Shooter Left  | 20     | SparkMax        | Leader   |
| Shooter Right | 21     | SparkMax        | Follower |

---

# 🟣 Climber

| Device        | CAN ID | Controller Type | Notes               |
| ------------- | ------ | --------------- | ------------------- |
| Climber Left  | 30     | SparkMax        | Soft limits enabled |
| Climber Right | 31     | SparkMax        | Inverted            |

---

# 🟡 Sensors (CAN-based only)

| Device            | CAN ID | Type | Notes    |
| ----------------- | ------ | ---- | -------- |
| CANcoder - Arm    | 50     | CTRE | Absolute |
| CANcoder - Intake | 51     | CTRE | Absolute |

---

# ⚡ Power & Control

| Device                 | CAN ID | Notes          |
| ---------------------- | ------ | -------------- |
| Power Distribution Hub | 60     | REV PDH        |
| Pneumatics Hub         | 61     | REV PH         |
| RoboRIO                | 0      | Not on CAN bus |

---

# 🧠 Naming Convention in Code

CAN IDs must match Constants.java:

Example:

```java
public static final class Intake {
    public static final int ROLLER_CAN_ID = 10;
    public static final int PIVOT_CAN_ID = 11;
}
```
