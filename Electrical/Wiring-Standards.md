# Wiring Standards

This document defines the required wiring standards for all competition and offseason robots.

These standards exist to:

- Improve reliability
- Reduce electrical failures at competition
- Make troubleshooting fast and predictable
- Maintain consistency across seasons

Failure to follow these standards may result in required rework.

---

# 🔒 General Wiring Principles

1. All wires must be:
   - Properly stripped (no exposed copper)
   - Fully seated in terminals
   - Securely strain-relieved
2. No electrical tape as a permanent solution.
3. No loose or floating components.
4. All components must be mechanically secured.
5. All wiring must be neat, routed intentionally, and zip-tied.

---

# 🔴 Power Wiring Standards

## Wire Gauge Requirements

| Application                  | Wire Gauge |
| ---------------------------- | ---------- |
| Main Battery Leads           | 6 AWG      |
| PDP/PDH to motor controllers | 10–12 AWG  |
| Low-current devices          | 18–22 AWG  |

Never undersize wire gauge.

---

## Crimping Standards

- Use ratcheting crimpers only.
- Perform pull test after every crimp.
- No solder-filled power lugs.
- Heat shrink required on all ring terminals.

---

## Power Distribution Layout

- High-current wiring routed separately from signal wires.
- Battery wires must not cross sharp edges.
- Use grommets when passing through metal.

---

# 🟡 CAN Bus Wiring Standards

## CAN Topology

- Daisy chain only.
- No star configurations.
- Termination resistor at each end (120Ω).
- Verify ~60Ω across CANH and CANL when powered off.

---

## CAN Wire Practices

- Use twisted pair wire.
- Keep CAN wiring away from motor power wires.
- Secure CAN connectors to prevent vibration disconnects.
- No loose WAGO connectors without strain relief.

---

## CAN Labeling

Each CAN device must have:

- CAN ID
- Subsystem name
- Label visible without removal

Example:
INTAKE PIVOT – ID 11

---

# 🟢 Signal Wiring (Encoders, Limit Switches, Sensors)

- Use ferrules for stranded wire in spring terminals.
- Avoid running signal wires parallel to high-current wires.
- Secure sensor wires to prevent tension on connectors.
- Label both ends of sensor cables.

---

# 🔵 Motor Controller Mounting

- All controllers must be mechanically secured.
- Mount on non-conductive surface or insulated standoffs.
- Maintain airflow for cooling.
- Avoid mounting directly next to heat-generating components.

---

# 🟣 Pneumatics Wiring (If Applicable)

- Solenoids labeled clearly.
- Tubing cut cleanly at 90°.
- No tubing under tension.
- Secure tubing away from moving parts.

---

# ⚫ Wire Management Standards

- Bundle wires by subsystem.
- Use braided loom or wire wrap for exposed runs.
- Zip ties trimmed flush.
- Service loops required for:
  - Moving arms
  - Intake pivots
  - Drivetrain modules

No tight wires under tension.

---

# 🧠 Colour Coding Standards

| Function         | Colour |
| ---------------- | ------ |
| 12V Power        | Red    |
| Ground           | Black  |
| CAN High         | Yellow |
| CAN Low          | Green  |
| Signal (general) | White  |

Follow this convention whenever possible.

---

# 🏷 Labeling Standards

All wiring must be labeled if:

- It connects to CAN
- It connects to a motor controller
- It connects to sensors
- It connects to pneumatic components

Labels must:

- Be printed or clearly written
- Match subsystem naming in code
- Be durable (heat shrink preferred)

---

# 🛠 Electrical Checklist Before Every Competition

- [ ] Battery leads tight
- [ ] Main breaker secure
- [ ] CAN bus resistance ~60Ω
- [ ] No loose connectors
- [ ] All motor controllers visible in hardware client
- [ ] No exposed copper
- [ ] All wires strain relieved
- [ ] Radio power secured

---

# 🚨 Common Failure Points

Most frequent issues seen at competition:

1. Loose CAN connectors
2. Poor crimps on ring terminals
3. No strain relief on intake wiring
4. Battery connector wear
5. Radio power disconnections

Check these first when debugging.

---

# 🔄 Change Control

Any major rewiring requires:

- Update to Electrical documentation
- Updated photos in build log
- Verification before robot bag/tag (if applicable)

---

# 📸 Recommended Practice

After wiring completion:

- Take high-resolution photos
- Store in season documentation
- Use for future reference

---

# Engineering Philosophy

We wire the robot as if:

- It will survive heavy defense
- It will be inspected by professionals
- We will need to repair it in 5 minutes

Clean wiring is not cosmetic — it is competitive advantage.
