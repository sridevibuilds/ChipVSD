# 🧩 Week 4 Task – CMOS Circuit Design (sky130-style)

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Workshop-brightgreen?style=for-the-badge)
![Participants](https://img.shields.io/badge/Participants-sridevibuilds-brightgreen?style=for-the-badge)

---

## 🎯 Objective
Understand transistor-level CMOS behavior and how device physics, sizing, and variations affect timing, slack, noise margins, and STA analysis.  

By simulating CMOS devices with SPICE (as in the sky130 workshop), you will bridge **real device behavior** with **STA abstractions**.

---

## 🧠 Why This Task Matters
This task deepens your understanding of how transistor-level circuit properties drive the timing behavior that STA analyzes.  

By completing these experiments, you will:

- Visualize **Id–Vds** and **VTC** behavior from transistor physics.  
- Understand **delay, noise margins, and robustness** under variation.  
- Observe how **supply voltage and transistor sizing** affect CMOS switching and STA slack.  

**Workshop Collateral:** [sky130CircuitDesignWorkshop (GitHub)](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
**Note:** Workshop enabled on VSDIAT platform.

---

## 🛠️ Task Components
You will perform the following SPICE simulation experiments:

| Step | Experiment | Description |
|------|------------|------------|
| 1 | MOSFET Behavior – Id vs Vds | Simulate NMOS; sweep Vds for different Vgs; plot Id vs Vds to see linear & saturation regions |
| 2 | Threshold Voltage Extraction & Velocity Saturation | Sweep Vgs vs Id; extract Vt (linear extrapolation); observe velocity saturation effects in short-channel devices |
| 3 | CMOS Inverter – VTC | Build CMOS inverter (PMOS + NMOS); sweep Vin; plot Vout vs Vin; determine switching threshold Vm |
| 4 | Transient Behavior – Rise/Fall Delays | Apply pulse input; measure rise and fall delays at Vdd/2 crossing |
| 5 | Noise Margin Analysis | From VTC, determine VIL, VIH, VOL, VOH; compute NML = VIL−VOL, NMH = VOH−VIH |
| 6 | Power-Supply & Device Variation | Vary Vdd and transistor sizing; observe effects on VTC, noise margins, and delays |

---

## 📦 Deliverables
Document your work in **Markdown or Jupyter Notebook**, mirroring sky130 repo style:

### 1. Introduction / Background
- Purpose of each experiment  
- Reason for Id vs Vds, VTC, transient, etc.

### 2. SPICE Netlists / Code
Include full SPICE netlists for:

- Id vs Vds  
- Id vs Vgs (Vt extraction)  
- CMOS inverter VTC  
- Transient rise/fall delay  
- Variation studies

### 3. Plots & Figures
For each experiment:

- Id vs Vds curves  
- Id vs Vgs curves  
- VTC curves  
- Transient waveforms  
- VTC under variation  

**Annotations:** Mark threshold points, switching points, noise margin points.

### 4. Tabulated Results
| Parameter | Value | Observation |
|-----------|-------|-------------|
| NMOS Vt | ... V | From Id–Vgs sweep |
| Switching Threshold (Vm) | ... V | Midpoint of VTC |
| Rise Delay (tPLH) | ... ns | From transient waveform |
| Fall Delay (tPHL) | ... ns | From transient waveform |
| NML | ... V | Noise margin low |
| NMH | ... V | Noise margin high |
| Variation Effects | Vm shifted ... | Supply/W/L changes impact |

### 5. Observations / Analysis
- What you see (e.g., onset of saturation, threshold shift)  
- Why it happens (device physics explanation)  
- How this ties to STA concepts (delay models, variation, timing margins)

### 6. Conclusions
- How transistor-level behavior constrains timing in real circuits  
- How variation or supply changes affect STA margins and critical paths

### 7. References / Citations
- sky130 PDK models & documentation  
- Any additional literature referenced for simulations

---

## 🔗 Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)

---

## 📈 Progress Tracker
| Week | Task Status |
|------|------------|
| Week 4 | CMOS Circuit Design – SPICE Simulations & Analysis |

