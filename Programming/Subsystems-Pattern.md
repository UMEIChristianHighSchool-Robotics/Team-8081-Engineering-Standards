# Subsystem Design Pattern

This document defines how subsystems must be structured.

Subsystems represent hardware. They are the foundation of our robot code.

---

# 🎯 Responsibilities of a Subsystem

A subsystem must:

- Own its motor controllers
- Own its sensors
- Contain closed-loop control logic
- Expose high-level methods
- Provide status methods

A subsystem must NOT:

- Read driver controller input
- Schedule commands
- Contain match strategy

---

# 📂 File Location

src/main/java/frc/robot/subsystems/

Each subsystem gets its own file.

Example:
- DriveSubsystem.java
- IntakeSubsystem.java
- ShooterSubsystem.java

---

# 🏗 Standard Subsystem Structure

Each subsystem should include:

1. Hardware declarations
2. Constructor (configure hardware)
3. Public control methods
4. Sensor access methods
5. Periodic updates (if needed)

---

# 🔌 Hardware Initialization

All hardware setup happens in constructor.

Example responsibilities:
- Set motor inversion
- Set idle mode
- Set current limits
- Set soft limits
- Configure PID

Never configure hardware in commands.

---

# 🎛 Public Methods

Public methods should represent actions.

Good examples:

- setSpeed(double speed)
- setPosition(double radians)
- stop()
- deploy()
- stow()

Bad examples:

- setMotorOutputRaw(double value)
- setCANFramePeriod(int value)

Subsystems expose intent, not implementation.

---

# 📊 Sensor Methods

Subsystems must expose:

- getPosition()
- getVelocity()
- atSetpoint()

Commands should not access motor objects directly.

---

# 🔁 Periodic()

Use periodic() only for:

- Telemetry
- Safety checks
- Logging

Do not place driver logic inside periodic().

---

# 🧪 Closed-Loop Control

PID, feedforward, and soft limits belong in the subsystem.

Commands should request actions, not compute control output.

Example:

Command:
shooter.setTargetRPM(4500);

Subsystem handles:
- PID
- Feedforward
- Motor output

---

# 🛑 Common Mistakes

❌ Reading controller buttons inside subsystem  
❌ Hardcoding constants  
❌ Returning motor objects publicly  
❌ Mixing teleop and autonomous logic  

---

# 🧠 Design Philosophy

Subsystems are stable.
Commands are flexible.

Subsystems change rarely.
Commands change often.

Keep subsystems clean and predictable.