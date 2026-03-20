# Constants Management

This document defines how constants are organized, named, and maintained in our robot code.

Proper constants management:

- Prevents magic numbers
- Makes tuning easier
- Reduces merge conflicts
- Improves readability
- Survives mentor and student turnover

All robot code must follow this structure.

---

# 🎯 Guiding Principles

1. No magic numbers in subsystem or command code.
2. All hardware IDs must exist in Constants.java.
3. All tunable values must be clearly labeled.
4. Constants must be grouped by subsystem.
5. Units must be clear and documented.

If a number might change — it belongs in Constants.

---

# 📂 File Structure

All constants live in:

src/main/java/frc/robot/Constants.java

Constants are grouped using nested static classes:

public final class Constants {

    public static final class Drive { }
    public static final class Intake { }
    public static final class Shooter { }
    public static final class Climber { }
    public static final class Auto { }

}

---

# 🏷 Naming Conventions

## Format

CONSTANT_NAMES_ARE_ALL_CAPS  
Words separated by underscores

Examples:

DRIVE_KP  
INTAKE_ROLLER_CAN_ID  
SHOOTER_MAX_RPM  

---

# 🔌 Hardware Constants

All hardware IDs must be declared in Constants.

Example:

public static final class Intake {
    public static final int ROLLER_CAN_ID = 10;
    public static final int PIVOT_CAN_ID = 11;
}

Do not hardcode CAN IDs inside subsystems.

---

# ⚙ PID Constants

PID constants must include units in comments.

Example:

public static final class Shooter {
    public static final double KP = 0.0005;   // RPM error → motor output
    public static final double KI = 0.0;
    public static final double KD = 0.0;
}

If using feedforward:

public static final double KS = 0.2;   // Static friction
public static final double KV = 0.001; // Velocity constant
public static final double KA = 0.0;   // Acceleration constant

---

# 📏 Units Standard

We use SI units whenever possible:

Distance → meters  
Velocity → meters per second  
Angle → radians  
Angular velocity → radians per second  
Time → seconds  

If using degrees, clearly label:

ARM_MAX_ANGLE_DEGREES

Never mix degrees and radians without explicit naming.

---

# 🧠 Setpoints and Tunable Values

All setpoints must be constants.

Example:

public static final class Intake {
    public static final double DEPLOYED_POSITION_RADIANS = 1.57;
    public static final double STOWED_POSITION_RADIANS = 0.0;
}

If a value is frequently tuned:

- Keep it in Constants
- Document what it controls
- Update Git commit message when changed

---

# 🚗 Drive Constants

Drive subsystem must include:

- Motor IDs
- Track width (meters)
- Wheel diameter (meters)
- Gear ratio
- Max speed (m/s)
- PID values
- Current limits

Example:

public static final class Drive {
    public static final double TRACK_WIDTH_METERS = 0.6;
    public static final double WHEEL_DIAMETER_METERS = 0.1016;
    public static final double MAX_SPEED_METERS_PER_SECOND = 4.5;
}

---

# 🔄 Auto Constants

All autonomous tuning constants belong in:

public static final class Auto { }

Include:

- Max auto speed
- Max auto acceleration
- Drive PID gains
- Rotation PID gains

Auto should not use teleop tuning values unless intentional.

---

# 🧪 Tuning Workflow

When tuning:

1. Change only one constant at a time.
2. Test on practice robot.
3. Record changes in commit message.
4. Push via pull request.
5. Do not tune directly on main branch.

---

# 🛑 What NOT To Do

❌ Hardcode values inside subsystem  
❌ Put constants inside commands  
❌ Duplicate constants across files  
❌ Mix units without labeling  
❌ Tune during competition without version tagging  

---

# 📊 Example Constants Structure (Full Example)

public final class Constants {

    public static final class Intake {
        public static final int ROLLER_CAN_ID = 10;
        public static final int PIVOT_CAN_ID = 11;

        public static final double KP = 1.2;
        public static final double KI = 0.0;
        public static final double KD = 0.1;

        public static final double DEPLOYED_POSITION_RADIANS = 1.4;
        public static final double STOWED_POSITION_RADIANS = 0.05;

        public static final int CURRENT_LIMIT_AMPS = 30;
    }

    public static final class Shooter {
        public static final int LEFT_CAN_ID = 20;
        public static final int RIGHT_CAN_ID = 21;

        public static final double TARGET_RPM = 4500;
        public static final double KP = 0.0006;
        public static final double KS = 0.2;
        public static final double KV = 0.00015;
    }
}

---

# 🔁 Updating Constants

When constants change:

- Update Constants.java
- Test thoroughly
- Update documentation if needed
- Commit with descriptive message

Example commit:

Adjust shooter KP from 0.0005 to 0.0006 for faster spin-up

---

# 🎓 Why This Matters

Good constants management:

- Makes debugging faster
- Makes tuning systematic
- Reduces merge conflicts
- Prevents hidden behavior
- Allows future teams to understand your design

Constants are part of the robot’s architecture.

Treat them with intention.