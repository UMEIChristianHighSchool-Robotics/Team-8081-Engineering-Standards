# Autonomous Strategy

This document defines how our team approaches autonomous design, implementation, testing, and competition execution.

Autonomous is a strategic advantage. It must be planned intentionally and tested rigorously.

---

# 🎯 Objectives of Autonomous

Our autonomous routine should:

1. Score guaranteed game pieces first.
2. Avoid risky actions early.
3. Position the robot advantageously for teleop.
4. Be consistent over flashy.
5. Be adjustable between matches.

Reliability > Complexity

---

# 🧠 Design Philosophy

We follow this priority order:

1️⃣ Guaranteed preload score  
2️⃣ Simple mobility bonus (if applicable)  
3️⃣ Low-risk additional game pieces  
4️⃣ Advanced routines only after consistency achieved

If a routine fails more than 10% of the time, it is not competition-ready.

---

# 📊 Strategy Planning Process

## Step 1: Game Analysis

After kickoff:

- Identify scoring value in autonomous
- Identify mobility or taxi bonuses
- Identify field symmetry
- Identify safe starting positions
- Determine cycle time limits

---

## Step 2: Define Autonomous Tiers

We categorize autos into tiers:

### Tier 1 – Baseline Auto (Required)

- Score preload
- Leave starting zone
- Works every match
- Minimal moving parts

### Tier 2 – Competitive Auto

- Score preload
- Acquire and score second piece
- Position for teleop

### Tier 3 – Advanced Auto

- Multi-piece auto
- Vision-assisted alignment
- High coordination requirements

We always finish Tier 1 before developing Tier 2.

---

# 🏗 Technical Architecture

We use WPILib Command-Based framework.

Autonomous commands are:

- Built using SequentialCommandGroup
- Broken into small reusable commands
- Reusable between auto and teleop when possible

Example structure:

- ScorePreloadCommand
- DriveForwardMeters
- IntakeGamePiece
- ShootCommand

Autos are composed, not rewritten.

---

# 📂 Code Organization

Autonomous code lives in:

src/main/java/frc/robot/commands/autonomous/

Each routine should be:

- Named clearly
- Self-contained
- Built from smaller commands

Example:

TwoPieceAuto.java
TaxiOnlyAuto.java
CenterStartAuto.java

---

# 🧪 Testing Process

Autonomous must be tested in stages:

## 1️⃣ Unit Testing

- Individual commands tested in teleop
- Drive distances verified
- PID tuned

## 2️⃣ Sequence Testing

- Run full auto with robot lifted
- Confirm order of operations

## 3️⃣ Field Testing

- Run full auto on practice field
- Verify timing
- Record success rate

## 4️⃣ Stress Testing

- Run 5–10 times consecutively
- Track failure percentage

---

# 📈 Success Metrics

An auto is competition-ready when:

- Success rate ≥ 90%
- No collisions with field elements
- No CAN errors
- No brownouts
- No unexpected behavior

If failure rate > 10%, revert to simpler version.

---

# 🎛 Auto Selection

We use:

- SendableChooser in RobotContainer
- Dashboard auto selection
- Clear naming (e.g., "2 Piece - Left")

Auto names must include:

- Number of pieces
- Starting position
- Special requirements

Example:
"2 Piece - Right - No Vision"

---

# 🔁 Iteration Between Matches

After each match:

- Review performance
- Identify timing issues
- Check starting alignment
- Adjust distances if necessary

All changes must go through Git workflow.

No last-second risky edits before playoffs.

---

# 🤝 Drive Team Coordination

Autonomous requires:

- Consistent starting alignment
- Clear communication with alliance partners
- Pre-match confirmation of selected auto

Before match:

- Confirm auto on dashboard
- Confirm alliance strategy
- Confirm starting position

---

# 🚨 Common Autonomous Failure Points

- Intake not fully deployed before driving
- Shooter not spun up before firing
- Gyro not zeroed
- Robot drift due to incorrect odometry
- Brownouts during simultaneous motor use

These must be validated before competition.

---

# 🧩 Sensor Strategy

We prefer:

- Encoders for distance
- Gyro for heading
- Vision only when reliable

Vision should enhance autos — not be required for baseline functionality.

---

# 🏁 Competition Rules

During competition:

- No major auto rewrites
- No experimental vision code
- Only small, controlled adjustments

Stability > Ambition

---

# 📚 Post-Event Review

After each competition:

Document:

- Which autos were used
- Success rate
- Failure causes
- Lessons learned

Update documentation for future seasons.

---

# 🧠 Engineering Philosophy

Autonomous wins matches.

It should be:

- Strategically chosen
- Carefully engineered
- Rigorously tested
- Calmly adjusted

We do not gamble on autonomous.
