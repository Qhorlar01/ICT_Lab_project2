# Speed-Controlled Two-Quadrant DC Motor Drive

[![MATLAB](https://img.shields.io/badge/MATLAB-R2023b-orange)](https://www.mathworks.com/products/matlab.html)

This project involves the design and simulation of a closed-loop speed-controlled two-quadrant DC motor drive using MATLAB. The system employs a three-phase phase-controlled rectifier for armature voltage control, cascaded PI controllers for current and speed regulation, and regenerative braking capabilities.

##  Project Overview
- **Objective**: Achieve precise speed control of a DC motor while maintaining safe operating limits.
- **Key Features**:
  - Two-quadrant operation (forward motoring and regenerative braking).
  - Closed-loop control with cascaded current and speed controllers.
  - MATLAB simulations for stability analysis (Bode plots, step responses).
- **Applications**: Industrial motor drives, electric vehicles, robotics.

## 🛠️ System Components
| Component                     | Function                                                                 |
|-------------------------------|--------------------------------------------------------------------------|
| Three-Phase AC Supply         | Provides 230V, 60Hz input power.                                         |
| Phase-Controlled Rectifier    | Converts AC to adjustable DC voltage (max 310.5V).                       |
| DC Motor                      | 220V, 8.3A armature; parameters: `Ra=4Ω`, `La=0.072H`, `J=0.0607 kg·m²`. |
| Tachometer                    | Measures motor speed for feedback.                                       |
| Current/Speed Controllers     | PI controllers with gains `Ki=2.33` (current) and `Kw=28.73` (speed).    |
| Limiter                       | Enforces a 20A current limit for safety.                                 |

##  Key Concepts
- **Two-Quadrant Control**: Allows motoring (forward direction) and regenerative braking.
- **Cascade Control**:
  - **Inner Loop**: Current controller adjusts rectifier firing angle (α).
  - **Outer Loop**: Speed controller generates current reference (iₐ*).
- **Regenerative Braking**: Converts kinetic energy to electrical energy during deceleration.

##  Design Steps
1. **Converter Design**:
   - Calculated converter gain: `Kr = 31.05 V/V`.
   - Transfer function: `Gr(s) = 31.05 / (1 + 0.00138s)`.
2. **Current Controller**:
   - Time constant `Tc = 0.0208s`, gain `Kc = 2.33`.
3. **Speed Controller**:
   - Total time constant `T4 = 0.0047s`, gain `K8 = 28.73`.
