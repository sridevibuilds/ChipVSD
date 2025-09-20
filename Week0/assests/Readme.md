## ⚙️ Tool Installation & Verification

**Tool Flow:** 🧠 Yosys → 📟 Iverilog → 📊 GTKWave → ⚡ Ngspice → 🎨 Magic VLSI

---

### 🧠 1. Yosys – RTL Synthesis Tool
**Purpose:** Converts RTL code into gate-level representations.

```bash
# Clone Yosys repository
git clone https://github.com/YosysHQ/yosys.git
cd yosys 

# Install dependencies
sudo apt install make
sudo apt-get install build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git \
graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev

# Build and install
make
sudo make install
```
📷 [Installation Verification:](https://github.com/sridevibuilds/ChipVSD/Week0/assests/yosysinstallation)
✅ Yosys Successfully Installed

### 📟 2. Iverilog – Verilog Simulator
**Purpose:** Compiles and simulates Verilog designs.

```bash
sudo apt-get install iverilog
```

---

### 📊 3. GTKWave – Waveform Viewer
**Purpose:** Visualizes simulation waveforms for debugging.

```bash
sudo apt update
sudo apt install gtkwave
```

---

### ⚡ 4. Ngspice – Circuit Simulator
**Purpose:** Performs analog and mixed-signal simulations.

```bash
sudo apt update
sudo apt install ngspice
```

---

### 🎨 5. Magic VLSI – Layout Tool
**Purpose:** Creates and analyzes VLSI layouts with DRC capabilities.

```bash
# Install dependencies
sudo apt-get install m4 tcsh csh libx11-dev tcl-dev tk-dev libcairo2-dev \
mesa-common-dev libglu1-mesa-dev libncurses-dev

# Clone Magic repository
git clone https://github.com/RTimothyEdwards/magic
cd magic

# Configure, build, and install
./configure
make
sudo make install
```

🚀 **Environment Ready for VLSI Design Journey!**
 
👨‍💻 Author: [sridevibuilds](https://github.com/sridevibuilds)  
📚 Program: VLSI System Design (VSD)

