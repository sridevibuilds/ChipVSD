# 📘 Week 3 – Post-Synthesis GLS & STA Fundamentals

[![License](https://img.shields.io/badge/license-MIT-blue)](../LICENSE)
[![Status](https://img.shields.io/badge/status-Completed-brightgreen)](#)

---

## 🎯 Objective
To understand and perform **Gate-Level Simulation (GLS)** after synthesis, validate the functionality,  
and get introduced to **Static Timing Analysis (STA)** concepts through practical experiments using **OpenSTA**.

---

## 🧩 Part 1 – Post-Synthesis GLS

### 🔹 Reference
- **GLS Flow & Methodology:** [VSD_HDP Example (Day 6)](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%206.md)

### 🔹 Steps
1. Perform **synthesis** of the *BabySoC* design.  
2. Run **Gate-Level Simulation (GLS)** using the synthesized netlist.  
3. Compare **GLS output** with **functional simulation output** (Week 2 task).  
   - The results should match.

### 🔹 Deliverables
- 🗂️ Synthesis logs  
- 🖼️ GLS waveform screenshots  
- 📝 Short note confirming **GLS = Functional Outputs**

---

## ⚙️ Part 2 – Fundamentals of STA (Static Timing Analysis)

### 🔹 Learning Resource
If STA is new, refer to this free foundational course on Udemy (valid for a limited time):

- [STA Fundamentals – Udemy Course](https://www.udemy.com/course/vlsi-academy-stachecks/?couponCode=F960AEDD365E0CD12546)

### 🔹 Focus Areas
- Setup and Hold checks  
- Slack  
- Clock definitions  
- Path-based analysis  

### 🔹 Deliverable
- A **one-page summary** or **key notes** from the STA course (bullet points preferred)

---

## ⏱️ Part 3 – Generate Timing Graphs with OpenSTA

### 🔹 Tools & References
- **OpenSTA GitHub:** [The-OpenROAD-Project/OpenSTA](https://github.com/The-OpenROAD-Project/OpenSTA)  
- **Example Script (Day 19):** [VSD_HDP Example](https://github.com/arunkpv/vsd-hdp/blob/main/docs/Day_19.md)  
- **Documentation:** [OpenSTA PDF Manual](https://github.com/The-OpenROAD-Project/OpenSTA/blob/master/doc/OpenSTA.pdf)

### 🔹 Steps
1. Load your **synthesized netlist** and **constraints** into OpenSTA.  
2. Generate **timing graphs** (setup/hold paths, slack, etc.).  
3. Capture at least one **timing report** and corresponding **graph**.

### 🔹 Deliverables
- 🧾 OpenSTA input scripts  
- 📊 Timing reports and graphs (screenshots with **userid** and **timestamp**)  
- 🧐 Observations:
  - What is the **critical path**?
  - What does the **slack** indicate?

---

## 🏁 Outcomes by the End of Week 3
By completing this week’s tasks, you will:
1. ✅ Perform **GLS** and validate functional correctness post-synthesis.  
2. ✅ Gain foundational knowledge of **STA**.  
3. ✅ Generate and analyze **timing graphs** using OpenSTA to interpret setup/hold paths and slack.

---
