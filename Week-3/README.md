# 🧩 Week 3 Task – Post-Synthesis GLS & STA Fundamentals  
## ⚙️ Part 1 – Post-Synthesis GLS (Gate-Level Simulation)

---

### 🎯 Objective  
To perform **Gate-Level Simulation (GLS)** after synthesis of the **BabySoC** design, validate the synthesized design’s functionality, and compare it with the **pre-synthesis functional simulation** (Week 2 task).

---

### 📘 Reference  
🔗 [GLS Reference – VSD_HDP (Day 6)](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%206.md)

---

### 🧩 Steps to Perform  

| Step | Description | Tool/Command |
|------|--------------|--------------|
| 1 | Perform synthesis of the BabySoC design | `yosys -s synth.ys` |
| 2 | Generate synthesized netlist (`.v` file) | Yosys output |
| 3 | Run Gate-Level Simulation (GLS) using the synthesized netlist and testbench | `iverilog` + `vvp` |
| 4 | Compare GLS output with functional simulation output (Week 2) | GTKWave |

---

### 🧠 Flow Description  

1. **RTL Synthesis:**  
   Use Yosys to synthesize the BabySoC RTL code and generate the gate-level netlist (`.v` file).  

2. **GLS Setup:**  
   Run simulation using the gate-level netlist with standard cell library and testbench.  

3. **Waveform Comparison:**  
   Observe output waveforms using GTKWave and compare with functional simulation results from Week 2.  

4. **Validation:**  
   Ensure outputs match for both functional and gate-level simulations.

---

### 📊 Example Commands  

```bash
# Step 1: Run synthesis
yosys -s synth.ys

# Step 2: Run gate-level simulation
iverilog -o gls_sim tb_babysoc.v babysoc_netlist.v
vvp gls_sim

# Step 3: View waveform
gtkwave gls_sim.vcd
```
📈 Observations

GLS waveform matches the functional simulation waveform from Week 2.

All signal transitions, timing behavior, and logic outputs are identical.

Confirms that synthesis preserved the original design intent.


✅ Verification Result:
The Gate-Level Simulation (GLS) output matches the functional simulation output, confirming that synthesis did not alter the intended logic or behavior of the design.
Therefore, GLS = Functional Output ✔️

🧠 Conclusion

Gate-Level Simulation validates the post-synthesis functionality of the BabySoC design.



# Week 3 Task – Post-Synthesis GLS & STA Fundamentals

## Part 2 – Fundamentals of STA (Static Timing Analysis)

### Objective
To understand the principles of **Static Timing Analysis (STA)** — verifying timing requirements of a digital circuit **without dynamic simulation** — using **OpenSTA**.

---

### Key Notes from STA Fundamentals (Udemy Course)

#### 1. Setup Time Check
- ⏱ Minimum time before the active clock edge that data must remain stable at the flip-flop input.  
- ❌ If data changes too late → **setup violation** → incorrect data capture.

#### 2. Hold Time Check
- ⏱ Minimum time after the clock edge during which data must stay stable.  
- ❌ If data changes too early → **hold violation** → race condition.

#### 3. Slack
- 📏 Indicates timing margin:  
  `Slack = Required Time – Arrival Time`  
- ✅ **Positive Slack (≥ 0):** timing met  
- ⚠️ **Negative Slack (< 0):** violation exists  
- 🔑 Slack helps identify **critical paths** that limit performance.

#### 4. Clock Definitions
Define clock period and source in constraint file (`.sdc`):
```tcl
create_clock -period 10 [get_ports clk]
set_input_delay 2 [get_ports data_in] -clock clk
set_output_delay 3 [get_ports data_out] -clock clk
```
⏰ Proper clock and I/O delay definitions are essential for accurate timing analysis.
5. Path-Based Analysis

STA examines all timing paths between:

🏁 Startpoints: input ports or launching flip-flops

🏁 Endpoints: output ports or capturing flip-flops

For each path, it computes setup and hold slacks.
Reports identify worst-case paths needing optimization.

6. STA Tool Flow (OpenSTA Example)
```tcl
read_liberty stdcell.lib
read_verilog design.v
read_sdc constraints.sdc
report_checks -path_delay min_max
```


📄 Generates timing reports showing arrival times, required times, and slack values.

Summary

STA ensures timing correctness without simulation.
Understanding setup, hold, slack, and clock definitions is vital for reliable chip performance.
Combined with Gate-Level Simulation (GLS), STA validates both functional and timing aspects of the synthesized design.

The matching outputs confirm the correctness of synthesis.

This step ensures that the synthesized netlist behaves identically to the original RTL before moving to Static Timing Analysis (STA).



# 🕒 Timing Graphs Using OpenSTA

## 1. Introduction
Timing is critical in digital CMOS circuits. Signals must propagate correctly within the clock period.  
Static Timing Analysis (STA) checks all paths without simulation vectors.

---

## 2. STA in CMOS Design Flow

| Stage | Purpose |
|-------|---------|
| RTL Design | Functional design in Verilog/VHDL |
| Synthesis | Gate-level netlist generation |
| Place & Route | Adds routing & interconnect delays |
| STA | Checks paths meet timing constraints |
| Optimization | Fix violations (resize cells, add buffers) |

---

## 3. What is OpenSTA?
OpenSTA is an open-source STA tool:  
- Reads Verilog netlists & Liberty libraries  
- Supports SDC constraints  
- Computes arrival, required times & slack  
- Reports critical paths  

[GitHub](https://github.com/The-OpenROAD-Project/OpenSTA)

---

## 4. Clock Modeling Features
- Single/multiple clocks ⏰  
- Clock uncertainty & jitter ⚡  
- Duty cycle, rise/fall times  
- Clock propagation through FFs/buffers  

Example:

create_clock -name clk -period 10 [get_ports clk]


# 🕒 Timing Graphs Using OpenSTA (Sections 5–13)

## 5. Exception Paths

- **False Paths ❌** – Paths that are logically impossible in actual operation and are ignored in STA.  
- **Multicycle Paths 🔁** – Paths allowed to span multiple clock cycles.  

**Example:**
```sdc
set_false_path -from [get_cells FF1] -to [get_cells FF2]
set_multicycle_path 2 -from [get_clocks clk] -to [get_clocks clk]
```

## 6. Delay Calculation

Total delay formula:

Total Delay = Cell Delay + Interconnect Delay


Early arrival → Used for hold checks

Late arrival → Used for setup checks

## 7. Timing Analysis & Reporting

OpenSTA commands:

```bash

read_liberty -min ./lib/standard.lib
read_verilog src/top.v
read_sdc constraints/constraints.sdc
update_timing
report_timing -max_paths 10
report_slack -max_paths 10
report_timing → Shows critical paths (setup & hold)
report_slack → Shows slack for each path

```



Setup paths – Data must arrive before the next clock edge

Hold paths – Data must not arrive too early

Critical path 🔺 – Path with minimum slack, most likely to fail timing

## 9. Setup & Hold Checks

Setup Check:

Arrival Time ≤ Required Time


Hold Check:

Arrival Time ≥ Required Time - Hold Time


Slack Calculation:

Slack
=
Required Time
−
Arrival Time
Slack=Required Time−Arrival Time

Positive slack ✅ → Timing met

Negative slack ❌ → Timing violation

## 10. Key Concepts
Symbol	Meaning
⏱	Arrival Time
⏳	Required Time
⚡	Slack
🔺	Critical Path
❌	False Path
🔁	Multicycle Path
## 11. Common SDC Constraints
# Clock definition
create_clock -name clk -period 10 [get_ports clk]

### Input delay for signals coming from outside
set_input_delay 2 -clock clk [get_ports data_in]

### Output delay for signals going outside
set_output_delay 1 -clock clk [get_ports data_out]

# Exceptions
set_false_path -from [get_ports reset] -to [get_ports data_out]
set_multicycle_path 2 -from [get_ports clk] -to [get_ports data_out]

## 12. Installation
Docker (Recommended)
```bash
sudo docker pull openroad/opensta:latest
sudo docker run -it --rm -v $(pwd):/work openroad/opensta:latest bash

Build from Source
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
mkdir build && cd build
cmake ..
make -j$(nproc)
```

## 13. Basic Inline Timing Analysis
### Load standard cell library
read_liberty -min ./lib/sky130_fd_sc_hd__tt_025C_1v80.lib

### Load Verilog design
read_verilog src/top.v

### Load constraints
read_sdc constraints/constraints.sdc

### Build timing graph
update_timing

### Report timing
report_timing -max_paths 5
report_timing -min_paths 5

### Report slack
report_slack -max_paths 5

# Example

## 1. Sample Verilog Module (src/top.v)
```
// Simple sequential design for STA demonstration
module top(
    input  wire clk,
    input  wire rst,
    input  wire [3:0] a,
    input  wire [3:0] b,
    output reg  [3:0] sum
);

    reg [3:0] r1;

    always @(posedge clk or posedge rst) begin
        if (rst)
            r1 <= 4'b0;
        else
            r1 <= a + b;
    end

    always @(posedge clk or posedge rst) begin
        if (rst)
            sum <= 4'b0;
        else
            sum <= r1;
    end

endmodule
```


### ✅ Explanation:

A simple 2-stage sequential adder

Includes flip-flops to create setup/hold timing paths

Easy to observe critical paths in OpenSTA

## 3. SDC Constraints (constraints/constraints.sdc)
### Clock definition
create_clock -name clk -period 10 [get_ports clk]

### Input delay for signals arriving from outside
set_input_delay 2 -clock clk [get_ports a b]

### Output delay for signals going outside
set_output_delay 1 -clock clk [get_ports sum]

### Reset is asynchronous, not part of timing paths
set_false_path -from [get_ports rst] -to [get_ports sum]

### Example multicycle path (optional)
set_multicycle_path 2 -from [get_ports a] -to [get_ports sum]

## 4. TCL Script for STA (scripts/timing_analysis.tcl)
### Load standard cell library
read_liberty -min ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

### Load Verilog design
read_verilog ../src/top.v

### Load constraints
read_sdc ../constraints/constraints.sdc

### Build timing graph
update_timing

## Report maximum and minimum timing paths
report_timing -max_paths 5
report_timing -min_paths 5

### Report slack
report_slack -max_paths 5


✅ Explanation:

Reads the Liberty file for cell delays

Loads the gate-level netlist (top.v)

Applies constraints from SDC

Reports critical paths and slack

## 5. Running OpenSTA (Docker Example)

Open terminal in your project folder:
```
sudo docker run -it --rm -v $(pwd):/work openroad/opensta:latest bash


Inside Docker:

cd /work/scripts
sta -exit -scripts timing_analysis.tcl


OpenSTA will output:

Setup and hold violations

Worst Negative Slack (WNS)

Critical paths
```
