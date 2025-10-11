# 🧩 Part 3 – Timing Closure & Final Verification

[![License](https://img.shields.io/badge/license-MIT-blue)](../../LICENSE)
[![Status](https://img.shields.io/badge/progress-Completed-brightgreen)](#)

---

## 🎯 Objective
To achieve **timing closure** by analyzing and fixing timing violations  
found during **Static Timing Analysis (STA)** and validating final design integrity  
through **re-synthesis and verification**.

---

## 📘 Reference
- **VSD OpenSTA – Day 8:** [Timing Closure Methodology](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%208.md)
- **OpenSTA Documentation:** [The OpenROAD Project – OpenSTA](https://github.com/The-OpenROAD-Project/OpenSTA)

---

## ⚙️ Steps to Perform Timing Closure

### 1️⃣ Analyze STA Results
From **Part 2**, use the generated timing reports (`setup_timing_report.txt`, `hold_timing_report.txt`)  
to identify **violating paths** and determine whether they are setup or hold issues.

> 🧩 **Setup violation:** Data arrives too late (path delay too long).  
> 🧩 **Hold violation:** Data arrives too early (path delay too short).

---

### 2️⃣ Apply Fixes for Violations

Depending on the violation type, apply appropriate fixes in your synthesis flow.

| Violation Type | Cause | Possible Fix |
|----------------|-------|---------------|
| 🕒 **Setup** | Long data path delay | Optimize logic, use higher drive cells, increase clock period |
| ⚡ **Hold** | Short data path delay | Insert delay buffers, balance routing paths, use slower cells |

After modifications, **re-run synthesis** to regenerate the netlist.

```bash
# Re-run synthesis after timing fixes
yosys -s synth_babysoc_timingfix.ys
write_verilog babysoc_netlist_fixed.v
```

---

### 3️⃣ Re-Run STA to Validate Fixes

Run **OpenSTA** again on the updated netlist:

```bash
# OpenSTA flow for validation
sta
read_liberty sta_inputs/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog babysoc_netlist_fixed.v
link_design babysoc
read_sdc sta_inputs/constraints.sdc

# Generate updated timing reports
report_checks -path_delay max > reports/fixed_setup_report.txt
report_checks -path_delay min > reports/fixed_hold_report.txt
report_tns > reports/fixed_tns_summary.txt
report_wns > reports/fixed_wns_summary.txt
```

✅ **Goal:** Achieve **WNS ≥ 0** and **TNS ≥ 0** across all corners.  
This ensures the design meets timing requirements.

---

### 4️⃣ Perform Final GLS (Post-Fix Validation)

To ensure no logical issues were introduced during timing fixes,  
perform a **Gate-Level Simulation (GLS)** again with the updated netlist.

```bash
# Final GLS simulation using the fixed netlist
iverilog -o gls_final babysoc_netlist_fixed.v testbench.v
vvp gls_final
```

Compare the new waveform against the previous functional simulation  
to ensure **functional equivalence** is maintained.

---

## 🧾 Deliverables

| Type | Description | File / Path |
|------|--------------|-------------|
| 🧱 **Fixed Netlist** | Updated gate-level design after timing closure | `babysoc_netlist_fixed.v` |
| 📊 **Updated Timing Reports** | Final STA results after fixes | `sta_reports/` |
| 🖼️ **Final GLS Waveforms** | Post-fix functional equivalence verification | `gls_waveforms/` |
| 📝 **Summary Note** | Final design status and closure remarks | `Timing_Closure_Report.md` |

---

## 📂 Suggested Folder Structure

```bash
week-3/
└─ part-3/
   ├─ README.md
   ├─ babysoc_netlist_fixed.v
   ├─ sta_reports/
   ├─ gls_waveforms/
   ├─ Timing_Closure_Report.md
   └─ assets/
```

---

## 🧠 Observations / Notes
- **Timing closure** ensures the chip can reliably operate at the intended frequency.  
- **Setup and hold violations** must both be zero for a sign-off-ready design.  
- Always re-run **GLS** after STA fixes to confirm **no logical mismatches** were introduced.  
- Proper timing closure bridges the gap between **functional correctness** and **physical feasibility**.

---

## 👩‍💻 Contributor
**(Sridevi Nimmala)** – Author
