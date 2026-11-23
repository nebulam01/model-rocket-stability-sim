# Model Rocket 2D Layout, CG/CP & Time-Dependent Stability Tool

An interactive Python simulation and visualization tool built with **Gradio**, **NumPy**, **SciPy**, and **Matplotlib** to evaluate model rocket static/dynamic stability margins, mass-derived Center of Gravity ($x_{\text{CG}}$), Barrowman Center of Pressure ($x_{\text{CP}}$), and time-dependent flight stability prior to launch.

## Key Features
- **Interactive Component & Geometry Selection:** Configure nose cone planform (*Ogive, Conical, Parabolic, Elliptical*), nose/body dimensions, fin geometry (*Trapezoidal, Elliptical*, 3 or 4 fins), structural wall thickness and density, payload mass/position, motor thrust profile, and crosswind speed.
- **2D Engineering Cross-Section:** Plots the airframe geometry, fin planform, mass-derived **CG**, Barrowman **CP**, and key flight summary metrics.
- **Physics-Based Flight & Stability Integration:** Solves a rigid-body 2-DOF pitch/vertical flight model using `scipy.integrate.solve_ivp` (`RK45`) with prescribed solid-motor thrust curves and propellant mass depletion.
- **Automated Stability Classification & Engineering Commentary:** Categorizes configurations into **Good**, **Borderline (Over-Stable / Wind-Sensitive)**, or **Unstable** with actionable design notes.

## Physics Model & Scope
- **Aerodynamics (CP & $C_{N\alpha}$):** Subsonic Barrowman-style normal force slope and center-of-pressure estimation for nose cone and fin surfaces, paired with a first-order zero-lift drag estimate ($C_{D0}$).
- **Mass & Center of Gravity ($x_{\text{CG}}$):** Computed from component geometry, material density, payload placement, and time-varying propellant mass during motor burn.
- **Trajectory & Stability Margin:** Evaluates stability margin in calibers ($\text{SM} = \frac{x_{\text{CP}}(t) - x_{\text{CG}}(t)}{d}$) over time under exponential standard atmosphere density and crosswind effects.

### Limitations & Assumptions
- Intended for **preliminary pre-launch design exploration and educational/engineering analysis**, not flight certification.
- Assumes subsonic flow regime, rigid-body airframe, simplified crosswind/pitch coupling, and does not yet model parachute deployment or multi-stage separation.

## How to Run

### Option 1: Google Colab (Recommended)
1. Upload `notebooks/2d-rocket-stability-barrowman-rk45.ipynb` to Google Colab.
2. Run all cells; Gradio will launch an interactive interface directly in the notebook and provide a temporary public URL.

### Option 2: Local Python Environment
```bash
git clone [https://github.com/](https://github.com/)<your-username>/model-rocket-stability-sim.git
cd model-rocket-stability-sim
pip install -r requirements.txt
python src/rocket_stability_sim.py
