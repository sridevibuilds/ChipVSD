# 🌟 Week 2 – BabySoC Fundamentals & Functional Modelling

![SoC](https://img.shields.io/badge/Topic-SoC%20Design-blue?style=for-the-badge)
![BabySoC](https://img.shields.io/badge/Learning-BabySoC-green?style=for-the-badge)
![Simulation](https://img.shields.io/badge/Tools-Icarus%20Verilog%20%7C%20GTKWave-orange?style=for-the-badge)

---

## 🔹 What is a System-on-Chip (SoC)?
A **System-on-Chip (SoC)** is like a **mini-computer inside one chip** 🖥️.  
It combines multiple components that were once separate chips into a **single, compact, power-efficient IC**.

---

## 🔹 Components of a Typical SoC
1. **🧠 CPU (Processor)**  
   - Executes instructions and controls the system.  
   - Example: ARM Cortex, RISC-V core.  

2. **💾 Memory**  
   - **ROM / Flash** → permanent program storage.  
   - **RAM** → temporary data storage for CPU.  

3. **⚡ Peripherals**  
   - Interfaces to the outside world.  
   - Examples: UART, SPI, I2C, GPIO.  

4. **🛣️ Interconnect (Bus / Network)**  
   - The “highway” that connects CPU ↔ Memory ↔ Peripherals.  
   - Examples: AMBA, AXI, AHB.  

---

## 🔹 Why BabySoC?
👉 **BabySoC** is a **simplified SoC model** for learning.  
- Only includes the **basic blocks** (CPU + small memory + a few peripherals).  
- Easy to understand without overwhelming complexity.  
- Like a **toy model car 🚗** you practice on before driving a real car.  

---

## 🔹 Functional Modelling
Before designing real hardware, we do **functional modelling**:

- 📜 **Describe behavior** in Verilog.  
- 🖥️ **Simulate** with Icarus Verilog.  
- 📊 **View signals** using GTKWave.  

✅ Helps ensure logical correctness **before RTL and physical design**.  

---

## 🔹 Why Functional Modelling is Important?
- ✔️ Detects errors early 🔍  
- ✔️ Saves time and cost 💰  
- ✔️ Ensures CPU ↔ Memory ↔ Peripherals work together 🔗  
- ✔️ Builds strong foundation for RTL, synthesis, and physical design 🏗️  

---

## 🔹 BabySoC Block Diagram

```mermaid
graph TD;
    CPU[🧠 CPU] -->|Bus| MEM[💾 Memory];
    CPU[🧠 CPU] -->|Bus| PERI[⚡ Peripherals];
    MEM -->|Interconnect| PERI;

