# 📅 Day 1

## 1️⃣ Introduction to Verilog RTL Design and Synthesis
Verilog RTL (Register Transfer Level) design is the process of describing digital circuits at the level of **registers** and **combinational logic**. Synthesis translates the RTL code into a **gate-level netlist** for FPGA or ASIC implementation.

**Key Points:**
- ⚡ Focus on how **data moves between registers** and is processed.
- 🛠️ Synthesis tools generate **technology-specific logic gates**.
- 🏎️ Efficient RTL coding improves **timing, area, and power**.

---

## 1.1 SKY130RTL D1SK1 L1: Introduction to Iverilog Design Testbench
A **testbench** is a simulation environment used to **verify RTL functionality**.  
**Iverilog** is an open-source Verilog simulator for compiling and running simulations.

**Key Points:**
- 🧪 Testbenches **stimulate the design** with inputs and check outputs.
- 💻 Iverilog supports **compiling multiple Verilog files**.
- 🔄 Workflow:
  1. Write RTL  
  2. Write Testbench  
  3. Compile with Iverilog  
  4. Run simulation  
  5. Check waveforms  

**Example: Compile & Run Iverilog**

    # Compile design and testbench
    iverilog -o my_design.vvp my_design.v my_testbench.v

    # Run simulation
    vvp my_design.vvp

    # Optional: View waveform using GTKWave
    gtkwave my_design.vcd

---

## Simulation Flow
The typical simulation flow in Verilog using Iverilog:

 <img width="1790" height="950" alt="Screenshot 2025-09-23 233511" src="https://github.com/user-attachments/assets/62fabdf0-de94-4e52-9dee-7f51ba67e88e" />

---

## Explanation of Each Step

**1. Design**  
- Your RTL Verilog code describing the circuit.  
- Defines how data flows and what logic operations are performed.  

**2. Test Bench**  
- Provides input signals and monitors outputs.  
- Ensures the design works correctly before hardware implementation.  

**3. Iverilog Compile & Run**  
- Compile RTL + testbench using Iverilog:  

      iverilog -o my_design.vvp my_design.v my_testbench.v
      vvp my_design.vvp

- Produces a VCD file recording signal changes.  

**4. VCD File (Value Change Dump)**  
- Stores time-based transitions of signals.  
- Example: Clock toggles, counter increments.  
- File extension: `.vcd`  

**5. GTKWave Visualization**  
- Opens the VCD file for waveform inspection:  

      gtkwave my_design.vcd

- Allows verification of design behavior visually.  

---

**Summary Flow:**  
Design -> Test Bench -> Iverilog Compile & Run -> VCD File -> GTKWave

This flow ensures your RTL design is **verified and ready** before synthesis for FPGA or ASIC.
