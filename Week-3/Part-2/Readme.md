# ⚡ Part 2 – Static Timing Analysis (STA) Fundamentals using OpenSTA

[![License](https://img.shields.io/badge/license-MIT-blue)](../../LICENSE)
[![Status](https://img.shields.io/badge/progress-Completed-brightgreen)](#)

---

## 🎯 Objective
To perform **Static Timing Analysis (STA)** using **OpenSTA**,  
analyze **timing paths** in the synthesized *BabySoC* netlist,  
and verify that all paths meet required **setup and hold constraints**.

---

## 📘 Reference
- **Tool:** [OpenSTA GitHub Repository](https://github.com/The-OpenROAD-Project/OpenSTA)
- **VSD OpenSTA Workshop:** [Day 7 – Timing Analysis Basics](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%207.md)

---

## ⚙️ Steps to Perform STA

### 1️⃣ Prepare the Inputs
Gather all required STA input files:

| File Type | Description | Example File |
|------------|--------------|---------------|
| 🧠 **Netlist** | Synthesized gate-level Verilog | `babysoc_netlist.v` |
| 🕓 **Timing Library** | Standard cell delay models | `sky130_fd_sc_hd__tt_025C_1v80.lib` |
| 🧭 **SDC File** | Timing constraints (clocks, input/output delays) | `constraints.sdc` |

Place these files in a folder named `sta_inputs/`.

---

### 2️⃣ Launch OpenSTA and Load Files

```bash
# Start OpenSTA
sta

# Load design and constraints
read_liberty sta_inputs/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog sta_inputs/babysoc_netlist.v
link_design babysoc

# Apply timing constraints
read_sdc sta_inputs/constraints.sdc
```

> 🧩 **Tip:** Ensure your `.sdc` file defines proper clock names and periods  
> matching the top module in your synthesized netlist.

---

### 3️⃣ Run Basic STA Reports

```bash
# View clock definitions
report_clocks

# Report setup (max delay) analysis
report_checks -path_delay max -fields {slew capacitance nets} -digits 3

# Report hold (min delay) analysis
report_checks -path_delay min -fields {slew capacitance nets} -digits 3

# View overall timing summary
report_tns
report_wns
```

✅ **TNS (Total Negative Slack)** and **WNS (Worst Negative Slack)**  
must be **≥ 0** for a fully timing-clean design.

---

### 4️⃣ Save Reports & Logs

```bash
# Save results
report_checks -path_delay max > reports/setup_timing_report.txt
report_checks -path_delay min > reports/hold_timing_report.txt
report_tns > reports/tns_summary.txt
report_wns > reports/wns_summary.txt
```

Store all STA reports inside the folder `sta_reports/`.

---

## 🧾 Deliverables

| Type | Description | File / Path |
|------|--------------|-------------|
| 🧱 **STA Input Files** | Netlist, library, and SDC | `sta_inputs/` |
| 📊 **Timing Reports** | Setup & Hold analysis reports | `sta_reports/` |
| 📝 **Summary Note** | Observations and conclusions | `STA_Observations.md` |

---

## 📂 Suggested Folder Structure

```bash
week-3/
└─ part-2/
   ├─ README.md
   ├─ sta_inputs/
   │   ├─ babysoc_netlist.v
   │   ├─ sky130_fd_sc_hd__tt_025C_1v80.lib
   │   └─ constraints.sdc
   ├─ sta_reports/
   ├─ STA_Observations.md
   └─ assets/
```

---

## 🧠 Observations / Notes
- STA ensures **timing integrity** without requiring dynamic simulation.  
- Positive slack values indicate that the design **meets timing**.  
- Negative slack implies **timing violations**, requiring fixes in synthesis or constraints.  
- Combining STA and GLS validates both **functional** and **temporal** correctness of your design.

---

## 👩‍💻 Contributor
**(Sridevi Nimmala)** – Author
