# Debugging Checklist

This document defines the official debugging process for robot issues.

When something breaks:
- Stay calm.
- Follow the checklist.
- Do not guess.
- Do not randomly change constants.
- Change one thing at a time.

Most problems are simple.

---

# 🧠 Debugging Philosophy

1. Check mechanical first.
2. Check electrical second.
3. Check software third.
4. Change only one variable at a time.
5. Reproduce the problem consistently.

Do not assume it is a code issue.

---

# 🚦 Step 1: Identify the Type of Failure

Is the problem:

- Robot will not enable?
- A subsystem not moving?
- Moving incorrectly?
- Intermittent?
- Only failing in autonomous?
- Only failing under defense?

Be specific.

---

# 🔌 Robot Will Not Enable

Checklist:

- [ ] Driver Station shows correct robot mode
- [ ] Robot is connected (green indicators)
- [ ] Battery voltage above 12V
- [ ] No brownout warnings
- [ ] All breakers seated
- [ ] Main breaker secure
- [ ] No CAN errors in console

If code-related:
- [ ] Build successful
- [ ] Deployed latest version
- [ ] No red errors in console

---

# 🟡 Subsystem Not Moving

Mechanical:

- [ ] Is anything physically blocking movement?
- [ ] Chain/belt intact?
- [ ] Shaft loose?
- [ ] Set screw tight?

Electrical:

- [ ] Motor controller powered?
- [ ] CAN device visible in hardware client?
- [ ] Correct CAN ID?
- [ ] Breaker tripped?
- [ ] Wiring secure?

Software:

- [ ] Correct command scheduled?
- [ ] Correct button binding?
- [ ] Motor inverted incorrectly?
- [ ] Current limit too low?
- [ ] Soft limits preventing movement?

---

# 🔴 Subsystem Moves Incorrectly

- [ ] Encoder direction correct?
- [ ] Motor inversion correct?
- [ ] PID constants reasonable?
- [ ] Units correct (meters vs inches)?
- [ ] Degrees vs radians mismatch?
- [ ] Soft limits set correctly?

Print values to Shuffleboard to verify.

---

# 🔵 CAN Bus Problems

Symptoms:

- Devices disappear randomly
- Robot disables unexpectedly
- CAN errors in console

Checklist:

- [ ] No duplicate CAN IDs
- [ ] All connectors fully seated
- [ ] Termination resistors present
- [ ] ~60Ω across CANH/CANL when powered off
- [ ] No damaged wires
- [ ] Wiggle test on connectors

Most CAN issues are physical.

---

# 🟣 Autonomous Failing

- [ ] Correct auto selected?
- [ ] Gyro zeroed?
- [ ] Starting position correct?
- [ ] Odometry reset?
- [ ] Setpoints updated?
- [ ] Intake deployed before driving?
- [ ] Shooter spun up before firing?

Test auto multiple times in a row.

---

# 🟤 Brownouts

Symptoms:

- Robot reboots
- Radio disconnects
- Motors cut out

Checklist:

- [ ] Battery healthy?
- [ ] Battery properly charged?
- [ ] Battery leads tight?
- [ ] No excessive current draw?
- [ ] Ramp rate configured?
- [ ] Current limits enabled?

Check Driver Station logs.

---

# ⚙ Encoder Problems

- [ ] Correct port configured?
- [ ] Conversion factor set?
- [ ] Reset position at startup?
- [ ] Absolute encoder offset set?
- [ ] Sensor plugged in fully?

Display encoder values live.

If value doesn't change → wiring issue likely.

---

# 🎮 Controller Issues

- [ ] Correct USB order?
- [ ] Button mapping correct?
- [ ] Axis deadband applied?
- [ ] Controller recognized in Driver Station?

---

# 🧪 Software Debugging Tools

Use:

- SmartDashboard / Shuffleboard
- Driver Station console
- Hardware client (REV / CTRE)
- Print statements (temporary)
- Simulation (when hardware unavailable)

Remove debug spam before competition.

---

# 🔍 Debugging Process Example

Bad approach:

"Let's increase the PID."

Good approach:

1. Confirm encoder reading.
2. Confirm motor inversion.
3. Confirm setpoint.
4. Confirm output being sent.
5. Adjust one constant.
6. Test again.

---

# 🧾 Logging Expectations

Before competition:

- Verify no error spam in console.
- Remove unused debug prints.
- Confirm no constant values are being overwritten.

---

# 🏁 Competition Pit Rapid Debug Checklist

If robot fails between matches:

1. Swap battery.
2. Check main breaker.
3. Check CAN connections.
4. Check loose wires.
5. Restart robot.
6. Verify correct auto selected.
7. Do not panic-edit code unless necessary.

Most issues are loose connections.

---

# 📈 After-Failure Review

If a failure occurs:

- Document what happened.
- Identify root cause.
- Fix permanently.
- Update documentation if needed.

Do not repeat preventable mistakes.

---

# 🛑 Rules During Competition

- No large refactors.
- No architectural rewrites.
- No experimental features.
- Only minimal controlled changes.

Stability > Innovation.

---

# 🎓 Engineering Mindset

Good debugging is:

- Calm
- Logical
- Methodical
- Documented

The best teams are not the teams that never fail.
They are the teams that diagnose quickly and recover.