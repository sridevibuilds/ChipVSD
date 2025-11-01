# 🧱 Week 6 – Physical Design Workshop (Sky130 × OpenLANE)

![RISC-V](https://img.shields.io/badge/RISC--V-SoC%20Tapeout-blue?style=for-the-badge&logo=risc-v)
![Sky130](https://img.shields.io/badge/Skywater--PDK-130nm-green?style=for-the-badge)
![OpenLANE](https://img.shields.io/badge/OpenLANE-RTL2GDS-orange?style=for-the-badge)

---

## 🎯 Objective
Perform hands-on **Physical Design labs** using the **Sky130 PDK** and **OpenLANE** flow inside a **pre-configured VDI image**, and understand the complete **RTL-to-GDS** process — from **standard-cell design** to **layout, DRC, and STA** validation.

---

## 🧠 Why This Task Matters
This workshop bridges your **theoretical VLSI concepts** with **real chip implementation**.  
It helps you explore:
- How **hierarchical digital blocks** integrate with **analog/mixed-signal IPs**
- The **interplay between layout, timing, and DRC/LVS**
- How **physical design decisions** affect **silicon reliability** and **sign-off**

By completing this week, you will gain a full understanding of how a design travels:
> RTL ➜ Synthesis ➜ Floorplanning ➜ Placement ➜ CTS ➜ Routing ➜ DRC ➜ STA ➜ GDSII

---

## ⚙️ Environment Setup

### 🧩 VDI Image
🔗 **Download:** [Physical Design Tools VDI Image](https://drive.google.com/file/d/1Ri30Yeqjyprv-rStHEScUMpKtw2JfVJe/view)  
Install via **Oracle VirtualBox** using the provided setup document.

### ✅ Proof of Setup
Include a screenshot of your running VDI showing:
<your_username>@vsd-pd:~$

yaml
Copy code

---

## 🧪 Workshop Outline

### 🧭 Sky130 Day 1 – Inception of Open-Source EDA
- How computers interpret hardware (HDL)
- QFN-48 Package overview – chip, pads, die, IPs
- Introduction to RISC-V and hardware flow
- From software applications to hardware logic

#### 🧰 SoC Design and OpenLANE
1. Components of open-source digital ASIC design  
2. Simplified RTL-to-GDS flow  
3. Introduction to OpenLANE & Strive chipsets  
4. Detailed ASIC design flow walkthrough  

#### 🧩 Get Familiar with EDA Tools
- OpenLANE directory structure  
- Design prep & synthesis  
- Review post-synthesis files  
- Git link reference and log interpretation  

---

### 🧱 Sky130 Day 2 – Floorplanning & Library Cells

#### 🧰 Chip Floorplanning Concepts
- Utilization factor and aspect ratio  
- Pre-placed cells & decoupling capacitors  
- Power planning and pin placement  
- Floorplan execution in OpenLANE and layout review in Magic  

#### 🔗 Library Binding and Placement
- Netlist binding and initial placement  
- Wire-length and capacitance-based optimization  
- Congestion-aware placement using RePlAce  

#### ⚡ Cell Design and Characterization
- Inputs to cell design flow  
- Circuit and layout design steps  
- Timing characterization flow  

---

### 🔬 Sky130 Day 3 – Magic Layout & ngspice Characterization

#### 🧠 CMOS Inverter Labs
- IO placer revision  
- SPICE deck creation and simulation  
- Switching threshold (Vm) and waveform analysis  
- Static and dynamic behavior  

#### 🏗️ Layout Fabrication Process Steps
- Formation of N/P wells, LDD, source/drain regions, metal layers  
- Creating standard cell layout and extracting SPICE  
- Sky130 tech-file introduction and DRC rule exercises  

---

### ⏱️ Sky130 Day 4 – Timing Analysis & Clock Tree Synthesis

#### 🧮 Timing Modelling & Delay Tables
- Grid-to-track conversion  
- Std cell LEF generation  
- Delay table creation and analysis  

#### 🕒 Timing Analysis with Ideal Clocks
- Setup time and clock jitter concepts  
- Post-synthesis timing with OpenSTA  
- Timing ECO and optimization  

#### 🌳 Clock Tree Synthesis (CTS)
- H-tree clock routing and buffering  
- Crosstalk reduction and shielding  
- CTS using TritonCTS and verification steps  

---

### ⚙️ Sky130 Day 5 – Routing & Final Sign-Off

#### 🧭 Routing and Design Rule Checks
- Introduction to Maze Routing – Lee’s Algorithm  
- Understanding DRC violations and fixes  

#### ⚡ Power Distribution Network (PDN)
- Power strap creation  
- Global and detailed routing with TritonRoute  

#### 🧩 TritonRoute Features & Post-Route Outputs
- Inter-guide connectivity and multi-layer routing  
- Routing topology algorithms  
- Final file list after routing  

---

## 📂 Deliverables

| # | Deliverable | Description |
|:-:|--------------|-------------|
| 1 | 🖥️ **Proof of VDI Setup** | Screenshot showing running VDI with your username |
| 2 | 📸 **Lab Documentation** | Screenshots + short explanations for each lab |
| 3 | 🧠 **Key Learnings** | Summarize per lab what you learned about PD flow |
| 4 | 🧩 **Inter-dependency Notes** | Describe how DRC, LVS, and STA interact |
| 5 | 💾 **GitHub Repo** | Push all documentation and screenshots to your repo |

---

## 🧭 Reference Documentation Style
📚 **Follow:** [Sample SoC Design and Planning Repo (NASSCOM × VSD)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/)

Each section should include:
- Objective  
- Commands or steps executed  
- Screenshot(s)  
- Observation or conclusion  

---

## 🏁 Week 6 Outcomes
✅ Successfully operated the **Physical Design VDI environment**  
✅ Executed the **RTL-to-GDSII flow** using OpenLANE + Sky130  
✅ Understood **floorplanning, placement, CTS, routing, DRC, STA**  
✅ Linked **digital and analog flows** for complete chip sign-off  

---
