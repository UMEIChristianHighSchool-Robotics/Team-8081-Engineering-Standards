# Robot Architecture

This document defines how our robot software is structured.

A clear architecture:
- Reduces bugs
- Makes debugging easier
- Supports multiple programmers
- Survives mentor turnover
- Enables safe competition changes

We use WPILib Command-Based architecture.

---

# 🧠 Architectural Philosophy

We follow these principles:

1. Subsystems represent hardware.
2. Commands represent robot actions.
3. RobotContainer wires everything together.
4. Constants define all configuration.
5. No hardware logic inside commands.
6. No driver logic inside subsystems.

Separation of concerns is mandatory.

---

# 🏗 High-Level Structure

src/main/java/frc/robot/

- Robot.java
- RobotContainer.java
- Constants.java
- subsystems/
- commands/

---

# 🤖 Robot.java

Robot.java should:

- Not contain subsystem logic
- Not contain button bindings
- Only manage robot lifecycle

Responsibilities:
- Call CommandScheduler
- Handle mode transitions
- Schedule autonomous command

Robot.java must remain minimal.

---

# 🎛 RobotContainer.java

RobotContainer is responsible for:

- Creating subsystem objects
- Creating controller objects
- Binding buttons to commands
- Setting default commands
- Providing autonomous command

RobotContainer should not contain:
- PID tuning
- Hardware configuration
- Complex logic

---

# 🧩 Subsystems

Subsystems:

- Represent physical hardware
- Contain motor controllers
- Contain sensors
- Expose public methods for actions
- Contain closed-loop control logic

Subsystems should NOT:
- Read controller inputs
- Schedule commands
- Make strategic decisions

---

# 🧾 Commands

Commands:

- Represent actions
- Call subsystem methods
- Control timing and sequencing
- Contain high-level logic

Commands should:
- Be small and focused
- Require only needed subsystems
- Avoid duplicating constants

---

# 🔄 Data Flow Model

Controller Input → Command → Subsystem → Hardware

Never:

Controller → Subsystem directly

---

# 🏁 Autonomous Structure

Autonomous routines are built using:

- SequentialCommandGroup
- ParallelCommandGroup

Autos must reuse teleop commands whenever possible.

No duplicated logic.

---

# 🎯 Default Commands

Each subsystem should have:

- A safe default command
- Teleop behavior defined clearly

Example:
- Drive subsystem → ArcadeDrive command
- Shooter → Idle/maintain speed

---

# 🔐 Dependency Rules

- Commands depend on Subsystems.
- Subsystems depend on Constants.
- Nothing depends on Commands.

Avoid circular dependencies.

---

# 🛑 Anti-Patterns

Do NOT:

- Put motor code in commands
- Put controller logic in subsystems
- Hardcode constants in commands
- Write massive multi-purpose commands
- Bypass CommandScheduler

---

# 🧠 Why Architecture Matters

A robot fails when code is chaotic.

A robot succeeds when:
- Roles are clear
- Code is modular
- Bugs are isolated
- Changes are controlled

Architecture is a competitive advantage.