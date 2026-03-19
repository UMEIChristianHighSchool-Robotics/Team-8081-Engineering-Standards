# Software Setup Guide

This guide walks new programmers through setting up their development environment for FRC robot programming.

Follow these steps in order.

If you encounter issues, ask a mentor before troubleshooting randomly.

---

# 💻 System Requirements

Recommended:

- Windows 10 or 11 (64-bit)
- 16GB RAM preferred (8GB minimum)
- 20GB free disk space
- Reliable internet connection

MacOS and Linux are supported but may require additional troubleshooting.

---

# 🟢 Step 1: Install WPILib

1. Go to the official WPILib website:
   https://docs.wpilib.org

2. Download the WPILib Installer for your operating system.

3. Run the installer:
   - Choose "Install for this User"
   - Select:
     - VS Code
     - C++ tools (optional if Java only)
     - Java JDK (required)
     - FRC Tools

4. Restart your computer after installation.

---

# 🟡 Step 2: Install Git

Download Git:
https://git-scm.com/downloads

During installation:

- Use default settings
- Choose "Git from command line and also from 3rd-party software"

Verify installation:

Open terminal and type:
git --version

---

# 🔵 Step 3: Install GitHub Desktop (Recommended for Beginners)

Download:
https://desktop.github.com/

Sign in using your GitHub account.

---

# 🟣 Step 4: Join the Team GitHub Organization

1. Accept invitation email.
2. Confirm access to:
   - Current season robot repo
   - Engineering Docs
   - Code Examples

If you cannot see repositories, notify a mentor.

---

# 🟠 Step 5: Clone the Robot Repository

Using GitHub Desktop:

1. Click "Clone Repository"
2. Select team robot repo
3. Choose a local folder (e.g., Documents/FRC)

Open the project in VS Code using:
Right-click folder → "Open with Code"

---

# 🧪 Step 6: Verify WPILib Installation

In VS Code:

Press:
Ctrl + Shift + P

Search:
"WPILib: Create New Project"

If this appears, installation was successful.

---

# 🤖 Step 7: Build the Project

Open the robot project folder.

In VS Code:

Press:
Ctrl + Shift + P

Select:
"WPILib: Build Robot Code"

The build must complete without errors.

---

# 🔌 Step 8: Connect to the Robot

When robot is available:

1. Connect to robot WiFi or USB.
2. Turn robot on.
3. In VS Code:
   - Ctrl + Shift + P
   - "WPILib: Deploy Robot Code"

Robot should restart and appear in Driver Station.

---

# 🛠 Recommended VS Code Extensions

Install:

- Java Extension Pack
- GitLens (optional but helpful)
- Error Lens (optional)

Do NOT install random Java build tools.

WPILib manages dependencies automatically.

---

# 📁 Folder Structure Overview

Key folders in robot project:

src/main/java/frc/robot/
Robot.java
RobotContainer.java
subsystems/
commands/

Never modify build.gradle unless instructed.

---

# 🔄 Updating WPILib (New Season)

At the start of each season:

- Install the new WPILib version.
- Do NOT manually update old projects.
- Create a fresh robot template.

---

# 🚨 Common Setup Problems

## ❌ Gradle Build Fails

Try:

- Restart VS Code
- Delete .gradle folder
- Ensure correct Java version installed

## ❌ Robot Not Deploying

Check:

- Driver Station connected
- Correct team number
- Robot powered
- Radio connected

## ❌ Git Not Recognized

Reinstall Git and restart computer.

---

# 📦 Simulation Testing

To run simulation:

Ctrl + Shift + P
Select:
"WPILib: Simulate Robot Code"

This allows testing without hardware.

---

# 🔐 Account Rules

- Use personal GitHub account.
- Do not share passwords.
- Enable 2-factor authentication.
- Do not push directly to main branch.

See Git-Workflow.md for contribution rules.

---

# 🎓 Learning Resources

Official Documentation:
https://docs.wpilib.org

Command-Based Programming:
https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html

REV Documentation:
https://docs.revrobotics.com

---

# 🧠 Before You Start Coding

New programmers must:

- Read Git-Workflow.md
- Understand Constants structure
- Review subsystem architecture document

---

# ✅ Setup Checklist

- [ ] WPILib Installed
- [ ] Git Installed
- [ ] GitHub Access Confirmed
- [ ] Project Cloned
- [ ] Code Builds
- [ ] Robot Deploy Successful

Once complete, notify Software Lead.
