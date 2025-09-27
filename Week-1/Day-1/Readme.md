# 📅 Day 1

## 1. Introduction to Verilog RTL Design and Synthesis
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

## 2. Lab: Simulating a 2-to-1 Multiplexer

Let’s simulate a simple **2-to-1 multiplexer** using iverilog!

###  Step 1: Clone the Workshop Repository

```shell
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
```

###  Step 2: Install Required Tools

```shell
sudo apt install iverilog
sudo apt install gtkwave
```

###  Step 3: Simulate the Design

Compile the design and testbench:

```shell
iverilog good_mux.v tb_good_mux.v
```

Run the simulation:

```shell
./a.out
```

View the waveform:

```shell
gtkwave tb_good_mux.vcd
```

<div align="center">
  <img src="https://github.com/user-attachments/assets/701e8189-3101-4a82-8134-e799521b9a8b" alt="GTKWave Example" width="70%">
</div>

---

## 3. Verilog Code Analysis

**The code for the multiplexer (`good_mux.v`):**

```verilog
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
```

###  **How It Works**

- **Inputs:** `i0`, `i1` (data), `sel` (select line)
- **Output:** `y` (registered output)
- **Logic:** If `sel` is 1, `y` gets `i1`; if `sel` is 0, `y` gets `i0`.

---

## 4. Introduction to Yosys & Gate Libraries

###  What is Yosys?

**Yosys** is a powerful open-source synthesis tool for digital hardware. It takes your Verilog code and converts it into a gate-level netlist—a hardware blueprint.

#### Yosys Features

- **Synthesis:** Converts HDL to a logic circuit
- **Optimization:** Improves speed or area
- **Technology Mapping:** Matches logic to actual hardware cells
- **Verification:** Checks correctness
- **Extensibility:** Supports custom flows

###  Why Do Libraries Have Different Gate "Flavors"?

A `.lib` file contains many versions of each gate (like AND, OR, NOT) with different properties:

- **Performance:** Faster gates for critical paths, slower for power savings
- **Power:** Some gates use less energy
- **Area:** Smaller gates for compact chips
- **Drive Strength:** Stronger gates to drive more load
- **Signal Integrity:** Specialized gates for noise/performance
- **Mapping:** Synthesis tools pick the best flavor for your needs

---

## 5. Synthesis Lab with Yosys

Let’s synthesize the `good_mux` design using Yosys!

###  Step-by-Step Yosys Flow

1. **Start Yosys**
    ```shell
    yosys
    ```

2. **Read the liberty library**
    ```shell
    read_liberty -lib /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

3. **Read the Verilog code**
    ```shell
    read_verilog /home/vsduser/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files/good_mux.v
    ```

4. **Synthesize the design**
    ```shell
    synth -top good_mux
    ```

5. **Technology mapping**
    ```shell
    abc -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

6. **Visualize the gate-level netlist**
    ```shell
    show
    ```
---

## 6. Summary

- You learned about simulators, designs, and testbenches.
- You ran your first Verilog simulation with iverilog and visualized waveforms.
- You analyzed the 2-to-1 mux code.
- You explored Yosys and learned why gate libraries have various flavors.


---
