# 🧩 Part 1 – Post-Synthesis Gate-Level Simulation (GLS)

[![License](https://img.shields.io/badge/license-MIT-blue)](../../LICENSE)
[![Status](https://img.shields.io/badge/progress-Completed-brightgreen)](#)

---

## 🎯 Objective
To perform **Gate-Level Simulation (GLS)** on the synthesized *BabySoC* design,  
validate its post-synthesis functionality, and confirm that **GLS outputs = Functional outputs** from Week 2.

---

## 📘 Reference
- **GLS Flow & Methodology:** [VSD_HDP Example – Day 6](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%206.md)

---

## ⚙️ Steps to Perform GLS

### 1️⃣ Perform Synthesis
Synthesize the *BabySoC* RTL design to generate the **netlist**.

```bash
# Example synthesis flow
yosys -s synth_babysoc.ys

# synth_babysoc.ys may contain commands such as:
read_verilog babysoc.v
synth -top babysoc
write_verilog babysoc_netlist.v
```

> **Deliverables →** store all synthesis logs in `synthesis_logs/`.

---

### 2️⃣ Run Gate-Level Simulation (GLS)
Simulate the synthesized netlist using your preferred simulator  
(e.g., **Icarus Verilog**, **Verilator**, or **ModelSim**).

```bash
# Example using Icarus Verilog
iverilog -o gls_sim babysoc_netlist.v testbench.v
vvp gls_sim
```

> 🧩 **Tip:** Ensure all necessary cell libraries are linked  
> (e.g., `sky130_fd_sc_hd.v`).

---

### 3️⃣ Compare GLS vs Functional Outputs
Re-run the Week 2 functional simulation and compare both waveform outputs.

✅ The **GLS waveform must match** the **functional waveform**.  
This confirms that synthesis preserved the design logic.

---

## 🧾 Deliverables

| Type | Description | File / Path |
|------|--------------|-------------|
| 🗂️ **Synthesis Logs** | Output logs from Yosys or your synthesis tool | `synthesis_logs/` |
| 🖼️ **GLS Waveform Screenshots** | Comparison between functional and GLS waveforms | `gls_waveforms/` |
| 📝 **Confirmation Note** | Short text confirming GLS = Functional outputs | `GLS_Verification.md` |

---

## 📂 Suggested Folder Structure

```bash
week-3/
└─ part-1/
   ├─ README.md
   ├─ synthesis_logs/
   ├─ gls_waveforms/
   ├─ GLS_Verification.md
   └─ assets/
```

---

## 🧠 Observations / Notes
- GLS simulation runs **slower** than functional simulation because it includes **gate delays**.  
- Matching waveforms verify that **synthesis did not alter** the logical behavior of the design.  
- Discrepancies indicate possible issues such as **missing constraints** or **incorrect timing libraries**.

---

## 👩‍💻 Contributor
**Zuna (Sridevi Nimmala)** – Author / Developer
