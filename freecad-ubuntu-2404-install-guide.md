# Installing FreeCAD 0.21 on Ubuntu 24.04 LTS: A Step-by-Step Guide & Dependency Fix

## 📝 Overview
This technical report documents the deployment of **FreeCAD 0.21.2** on **Ubuntu 24.04 (Noble Numbat)**. It covers the transition from standard repositories to the Official PPA, handling missing dependencies, and verifying the installation for engineering use.

---

## 🛠️ System Specifications
- **Operating System:** Ubuntu 24.04.3 LTS (Noble Numbat)
- **Architecture:** x86_64
- **Kernel:** Linux 6.8 (Standard for Noble)
- **Target Software:** FreeCAD 0.21 (Stable)

---

## 🚀 Installation Process

### Step 1: Environment Preparation
The system was updated to ensure compatibility with the new libraries and clear any previous conflicts.

```bash
sudo apt update && sudo apt autoremove freecad
```
###  Step 2: Adding the Official PPA

Default Ubuntu repositories often contain outdateded:
 CAD versions. To ensure access to the latest features, the Official FreeCAD Stable PPA was added:


```
sudo add-apt-repository ppa:freecad-maintainers/freecad-stable

```
Note: The system automatically refreshed the package lists after adding the repository on Ubuntu 24.04.
### Step 3: Deployment & Dependency Management

The initial goal was to install the core application, offline documentation, and the FEM engine.

Initial Command:
```
sudo apt install freecad freecad-doc calculix-ccx
```
⚠️ Troubleshooting: The "Missing Package" Issue
Problem

During Step 3, the terminal returned the following error: E: Unable to locate package freecad-doc
Root Cause Analysis

In the Ubuntu 24.04 (Noble) release, the freecad-doc package is not available under that specific name in the stable PPA branch or has been moved to a different distribution method. In Linux, if apt cannot find one package in a list, it halts the entire process.
Solution

The installation was re-executed by decoupling the documentation, focusing on the core binary and the CalculiX engine for engineering analysis:
```
sudo apt install freecad calculix-ccx
```
Result: Successful installation. Documentation remains accessible via the online Wiki (F1 shortcut).
🏁 Final Verification

The installation was verified using the CLI:
```
freecad --version
```
Output:

    FreeCAD 0.21.2 Revision: 33771 (Git)

💡 Key Takeaways for Linux Lab

PPA Priority: Using the Maintainers' PPA is critical for CAD work to avoid the "stale" versions in LTS repos.

Dependency Decoupling: When a non-essential package (like offline docs) fails, proceed with the core binary to maintain workflow.

Engineering Ready: By installing calculix-ccx, the environment is fully equipped for Finite Element Analysis (FEA/FEM).

Author: Juan Becerra

Project: Linux Learning & Documentation

Repository: linux-lab-notes

Date: January 2026
