# 🧪 Week 4 – Day 5: CMOS Power-Supply & Device Variation – Ngspice + sky130

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![Day 5](https://img.shields.io/badge/Day-5-orange?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)

---

## 🎯 Objective
- Evaluate CMOS inverter behavior under **power-supply variations** (Vdd)  
- Investigate impact of **device parameter variations** (W/L, oxide thickness, process)  
- Understand how variations affect **VTC, noise margins, and delays**  
- Connect **device-level variation** to **STA timing and robustness**  

---

## 📚 Lectures / Tasks with Briefs
| Lecture | Topic | Brief Description |
|---------|------|-----------------|
| 44-L1 | SPICE simulation for power supply variations | Simulate inverter with Vdd = 1.6 V, 1.8 V, 2.0 V. |
| 45-L2 | Advantages/disadvantages using low supply voltage | Analyze impact on delay, noise margin, and robustness. |
| 46-L3 | Sky130 Supply Variation Labs | Hands-on lab: plot VTC under different Vdd. |
| 47-L1 | Sources of variation – Etching process | Discuss manufacturing process variations. |
| 48-L2 | Sources of variation – Oxide thickness | Effect of oxide thickness variations on transistor parameters. |
| 49-L3 | SPICE simulation for device variations | Simulate effect of W/L, Vt, and other variations. |
| 50-L4 | Conclusion | Summarize effects of supply & device variation on CMOS robustness. |
| 51-L5 | Sky130 Device Variation Labs | Hands-on lab for device variation simulations. |

---

## 💻 SPICE Netlist Example

### CMOS Inverter with Vdd Variation
.include sky130_fd_pr__nfet_01v8.lib
.include sky130_fd_pr__pfet_01v8.lib
M1 out in vdd vdd sky130_fd_pr__pfet_01v8 W=2u L=0.15u
M2 out in 0 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vdd vdd 0 1.6
.dc Vin 0 1.8 0.01
.print dc v(out)
.end

### CMOS Inverter Device Variation
* Vary PMOS W/L
.include sky130_fd_pr__nfet_01v8.lib
.include sky130_fd_pr__pfet_01v8.lib
M1 out in vdd vdd sky130_fd_pr__pfet_01v8 W=3u L=0.15u
M2 out in 0 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vdd vdd 0 1.8
.dc Vin 0 1.8 0.01
.print dc v(out)
.end

---

## 📊 Plots / Figures
- VTC curves under **different Vdd values**  
- VTC curves for **device variations (PMOS/NMOS sizing)**  
- Annotated **switching thresholds, NML, NMH**  
- Compare curves to highlight **variation effects**  

---

## 🔍 Observations & Analysis
- Reducing Vdd → slower transition, smaller noise margins  
- Increasing Vdd → sharper transition, higher noise margins  
- Larger PMOS W/L → shifts Vm, affects NML/NMH  
- Device and supply variations directly affect **propagation delays** and **STA slack**  

---

## ✅ Conclusion
- CMOS inverter robustness is sensitive to both **supply voltage** and **device variations**  
- SPICE simulations help visualize these effects for **realistic STA modeling**  
- Understanding variation impacts is crucial for **timing closure** in digital design  

---

## 🔗 Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)
