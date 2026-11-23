# 🚀 2D Rocket Layout, CG/CP & Time-Dependent Stability Tool

An interactive simulation and visualization tool I built in Google Colab using **Gradio**, **NumPy**, **SciPy**, and **Matplotlib** to check model rocket stability, mass-derived Center of Gravity ($x_{\text{CG}}$), Barrowman Center of Pressure ($x_{\text{CP}}$), and time-dependent flight stability before any launch.

## ✨ Key Features
- **Interactive Component & Geometry Setup:** Pick nose cone shape (*Ogive, Conical, Parabolic, Elliptical*), nose/body dimensions, fin geometry (*Trapezoidal, Elliptical*, 3 or 4 fins), wall thickness and material density, payload mass/position, solid motor curve, and crosswind speed.
- **2D Engineering Cross-Section:** Draws the 2D rocket profile, fin planform, mass-derived **CG**, Barrowman **CP**, and key flight summary numbers right on the canvas.
- **Physics-Based Flight & Stability Solver:** Integrates a rigid-body 2-DOF pitch/vertical flight model with `scipy.integrate.solve_ivp` (`RK45`) using motor thrust profiles and propellant mass burn-off.
- **Automated Stability Status & Engineering Notes:** Classifies designs as **Good**, **Borderline (Over-Stable / Wind-Sensitive)**, or **Unstable**, with practical engineering feedback and explicit model assumptions.

## 🛠️ Tech Stack
- **Environment:** Google Colab (no local OpenRocket install needed)
- **Simulation & Plotting:** Python, Gradio, NumPy, SciPy (`solve_ivp` / `RK45`), Matplotlib

## ⚙️ How to Run the Project
1. **Open in Google Colab:**
   - Upload `2d-rocket-stability-barrowman-rk45.ipynb` to Google Colab (`colab.research.google.com`).
2. **Run & Launch the UI:**
   - Run the notebook cells; Gradio will install dependencies (`gradio`, `matplotlib`, `numpy`, `scipy`) and open the interactive interface right below the cell (plus a temporary `gradio.live` link if you want a bigger view).
3. **Explore & Iterate:**
   - Tweak geometry, materials, motor, or wind sliders/dropdowns and hit **Simulate & Plot** to see the 2D layout, stability-over-time curve, and status commentary update live.

## 📌 Scope & Assumptions
- Built for **pre-launch design exploration and engineering analysis**, not flight certification.
- Uses a subsonic Barrowman CP estimation, rigid-body 2-DOF pitch/vertical dynamics, exponential standard atmosphere density, and prescribed motor thrust profiles (parachute deployment and multi-stage separation are not modeled yet).
