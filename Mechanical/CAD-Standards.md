# CAD Standards

This document defines mechanical CAD standards for all robot designs.

Clean CAD:
- Prevents manufacturing errors
- Reduces assembly confusion
- Improves documentation
- Supports future seasons

CAD must be professional and organized.

---

# 🧠 CAD Philosophy

We design for:

- Serviceability
- Strength
- Manufacturability
- Weight efficiency
- Electrical accessibility

Good CAD reduces pit stress.

---

# 📁 File Organization

CAD files must be organized by:

- Subsystem
- Version
- Season

Example folder structure:

2026/
  Drivetrain/
  Intake/
  Shooter/
  Climber/

No random file names.

---

# 🏷 Naming Conventions

Parts must be named clearly.

Bad:
- Part1
- Plate_v2_final
- thing

Good:
- Intake_Pivot_Plate_Left
- Shooter_Mount_Bracket
- Drivetrain_Rail_Right

Assemblies must include subsystem name.

---

# 📐 Units

All CAD must use:

Millimeters (mm)

Never mix units.

---

# 🧩 Assembly Standards

Assemblies must:

- Fully constrain parts
- Avoid floating components
- Avoid unnecessary mates
- Represent real-world fastening

Bolts should be modeled where important.

---

# 🔩 Hardware Standards

Use standard hardware whenever possible:

- #10-32
- 1/4-20
- 1/8” rivets

Avoid random hardware sizes.

Minimize tool changes.

---

# ⚖ Weight Tracking

Major subsystems must track:

- Estimated weight
- Center of mass impact

Monitor weight throughout build season.

---

# 🔌 Electrical Integration

CAD must include:

- Motor locations
- Controller mounting space
- Wire routing paths
- Access to main breaker
- Battery clearance

Electrical must review CAD before fabrication.

---

# 🛠 Serviceability

Design so that:

- Motors can be replaced quickly
- Chains can be tensioned easily
- Gearboxes are accessible
- Electronics are reachable

Assume repairs will happen under time pressure.

---

# 📸 Release Process

Before manufacturing:

- CAD reviewed by mechanical lead
- Electrical consulted
- Fasteners verified
- Clearance checked
- Export manufacturing drawings

No part is cut without review.

---

# 🔄 Version Control

CAD files must:

- Be stored in team cloud
- Follow version naming
- Avoid overwriting major revisions

Document major design changes.

---

# 🎓 Engineering Mindset

CAD is not art.
It is communication.

If someone else cannot:
- Understand it
- Manufacture it
- Repair it

It is not complete.