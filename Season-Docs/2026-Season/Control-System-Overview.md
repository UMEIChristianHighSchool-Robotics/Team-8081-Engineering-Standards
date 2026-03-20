# Control System Overview  
## 2026 Robot – "Ark"

This document provides a high-level overview of the control system architecture for the 2026 robot, Ark.

Its purpose is to:

- Describe how hardware and software interact
- Document electrical and CAN layout
- Provide a reference for troubleshooting
- Preserve institutional knowledge for future seasons

Ark was designed with simplicity, serviceability, and reliability as core priorities.

---

# 🧠 Control System Philosophy

Ark follows these design principles:

- Mechanical simplicity first
- Modular subsystems
- Clean CAN organization
- Clear separation between hardware and software
- Serviceability under competition pressure

The control system prioritizes robustness over complexity.

---

# 🔌 Core Hardware

## RoboRIO
- RoboRIO 2.0
- All software deployed using WPILib (Java, Command-Based)

## Power Distribution
- REV Power Distribution Hub (PDH)
- Main breaker mounted for quick access
- Battery secured with vibration isolation

## Radio
- Competition radio powered through regulated 12V port
- Ethernet secured with strain relief

---

# 🚗 Drivetrain System

## Mechanical Configuration
- 6-wheel tank drive
- 4 driven wheels (center drop configuration)
- Chain-driven outer wheels
- 6 traction wheels
- 12:1 gear ratio per kitbot calculations

## Motor Configuration
- 4x NEO Vortex motors
- 4x Spark MAX motor controllers

### CAN Allocation Range
2–5 reserved for drivetrain

## Software Architecture
- DriveSubsystem
- Default command: DriveCommand
- Default drive mode: arcade drive (selectable tank drive in Shuffleboard)
- Closed-loop velocity control
- Current limiting enabled
- Ramp rate configured to reduce brownouts

---

# 🟢 Intake System

## Overview
The intake subsystem includes:

- Roller for game piece acquisition
- Pivoting arm for deployment and stowing

---

## Intake Roller

### Hardware
- 1x NEO Brushless motor
- 1x Spark Flex motor controller

### CAN Range
6 & 10 reserved for intake

### Control
- Open-loop control for roller
- Current limiting enabled
- Idle mode: Coast
- 2:1 gear ratio

---

## Intake Pivot

### Hardware
- 1x NEO motor
- 1x Spark MAX motor controller
- 1x Duty Cycle Encoder connected directly to RoboRIO DIO
- 180:1 gear ratio

### Sensor Configuration
- Duty cycle encoder wired to DIO port
- Absolute position used for arm reference
- Position conversion factor set in software
- Offset applied during initialization

### Control Strategy
- Closed-loop position control
- PID configured in subsystem
- Soft limits enforced in software
- Feedforward applied only when robot enabled

Pivot must not move unexpectedly on enable.

---

# 🔴 Shooter System

## Overview
- 4-wheel roller shooter
- 2 motors total (one per side)
- Wheels mechanically linked per side

## Hardware
- 2x Brushless motors
- 2x Spark MAX controllers

### CAN Range
12-13 reserved for shooter

## Control Strategy
- Velocity-based closed-loop control
- PID + feedforward tuning
- Right motor inverted

Shooter spin-up stability prioritized over aggressive acceleration.

---

# 🟡 Sensors

|        Sensor        |   Location   |      Interface      |
|----------------------|--------------|---------------------|
|  Duty Cycle Encoder  | Intake Pivot |     RoboRIO DIO     |
|    Motor Encoders    |  Integrated  |   Spark MAX / Flex  |

All sensors must be validated at startup.

---

# 🟣 CAN Bus Layout

## CAN Topology
Daisy-chain configuration:

PDH → Drive Motors → Intake → Shooter → (End termination)

- 120Ω termination at both ends
- No star topology
- Target bus utilization < 70%

See CAN-ID-Map.md for full allocation.

---

# 🧩 Software Architecture

Ark uses WPILib Command-Based structure:

## Subsystems
- DriveSubsystem
- IntakeSubsystem
- ShooterSubsystem

## Commands
- DriveCommand
- RunIntakeRollerCommand
- ReverseIntakeRollerCommand
- IntakeDownCommand
- IntakeUpCommand 
- IntakeTravelCommand
- HoldShootCommand
- ShooterIdleCommand
- TaxiOnlyAutoCommand
- TaxiShootAutoCommand
- TwoPieceAutoCommand
- SweepAutoCommand

## Constants
All:
- CAN IDs
- PID values
- Soft limits
- Setpoints
- Current limits

Defined in Constants.java.

No magic numbers permitted in subsystems.

---

# ⚡ Power & Current Strategy

To prevent brownouts:

- Current limits enabled on all brushless motors
- Ramp rate applied to drivetrain
- Shooter acceleration controlled
- Avoid simultaneous peak current draws during auto

Battery health monitored before every match.

---

# 🧪 Autonomous Readiness

Autonomous routines:

- Built from reusable commands
- Do not duplicate teleop logic
- Require pivot zero confirmation
- Tested minimum 5 consecutive runs

Auto selection via SendableChooser.

---

# 🔐 Safety Systems

- Intake pivot soft limits
- Current limiting on all motors
- Default commands stop motors when inactive
- Shooter only runs when commanded
- Manual override commands available

---

# 📸 Documentation Requirements

Before competition:

- Electrical layout photographed
- CAN chain photographed
- Firmware versions recorded
- Version tag created in GitHub

---

# 🏁 Pre-Competition Verification

- All CAN devices visible
- Duty encoder reading correctly
- Pivot zero confirmed
- Shooter reaches target RPM
- Drivetrain drives straight
- No console errors
- Autonomous tested successfully

---

# 🧠 System Summary

Ark’s control system is designed to be:

- Simple
- Reliable
- Modular
- Easy to debug
- Easy to service

Mechanical stability supports electrical clarity.
Electrical clarity supports software stability.
Software stability supports match performance.

Reliability is a strategic advantage.