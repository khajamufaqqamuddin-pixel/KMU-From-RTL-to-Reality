# ⚙️ VSD Hardware Design Program

## 🔰 Introduction to Verilog RTL Design and Synthesis

This repository documents my hands-on learning and implementation of Verilog-based RTL design and synthesis, using open-source tools like **Icarus Verilog**, **GTKWave**, and **Yosys**, with the Sky130 process node.

---

## 📚 Table of Contents

- 📌 [Introduction](#📌-introduction)
- 🧪 [RTL Simulation Flow (Icarus Verilog)](#🧪-rtl-simulation-flow-iverilog)
- 📁 [File Structure: MUX 2:1 Design](#📁-file-structure-mux-21-design)
- 🧬 [Yosys Synthesis Flow](#🧬-yosys-synthesis-flow)
- 🧾 [Key Learnings](#🧾-key-learnings)
- 📷 [Simulation & Synthesis Snapshots](#📷-simulation--synthesis-snapshots)

---

## 📌 Introduction

### 💡 RTL Design
- Written in Verilog to describe hardware behavior.

### 🧪 Testbench
- Applies stimulus and checks outputs.
- No primary I/O ports.

### 🔄 Simulator: Icarus Verilog (`iverilog`)
- Reacts to signal changes only (event-driven simulation).
- Generates `.vcd` waveform files for visual inspection.

---

## 🧪 RTL Simulation Flow (Icarus Verilog)

### ⚙️ Flow Diagram:















📊 **Flow Image**  
![Iverilog Flow](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/Iverilog_based_simulation_flow.png)

---

## 📁 File Structure: MUX 2:1 Design

### 🔧 Design: `good_mux.v`

🟢 Implements 2:1 multiplexer  
📥 Inputs: `i0`, `i1`, `sel`  
📤 Output: `y`  

- Behavioral Verilog using `always @(*)` with `if-else`.

🖼️ ![good_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/good_mux.jpeg)

---

### 🧪 Testbench: `tb_good_mux.v`

🎯 Stimulates the `good_mux` module.  
📝 Dumps waveforms for GTKWave via `$dumpfile` and `$dumpvars`.

🖼️ ![tb_good_mux](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-1/Day-1/good_mux_gtkwave.jpeg)

---

## 🧬 Yosys Synthesis Flow

🎯 Goal: Convert RTL → Gate-level netlist using Sky130 library

### 🧾 Yosys Synthesis Steps

```bash
# Step 0: Start Yosys
yosys

# Step 1: Load Sky130 Liberty file
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# Step 2: Load RTL Design
read_verilog good_mux.v

# Step 3: Perform RTL Synthesis
synth -top good_mux

# Step 4: Map to Technology Cells
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# Step 5: View Schematic
show

# Step 6: Export Netlist
write_verilog -noattr good_mux_netlist.v


