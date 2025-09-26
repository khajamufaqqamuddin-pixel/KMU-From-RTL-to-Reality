# 📘 VSD Hardware Design Program

## Topic: GLS, Blocking vs Non-Blocking & Synthesis-Simulation Mismatch

---

## 📚 Contents

- [🔍 Overview](#overview)
- [🔧 Synthesis of Ternary Operator MUX](#synthesis-of-ternary-operator-mux)
- [🧪 GLS of Ternary Operator MUX](#gls-of-ternary-operator-mux)
- [🚨 Synthesis of Bad MUX Design](#synthesis-of-bad-mux-design)
- [⚙️ GLS of Bad MUX Design](#gls-of-bad-mux-design)
- [⚠️ Synthesis-Simulation Mismatch (Bad MUX)](#synthesis-simulation-mismatch-bad-mux)
- [📉 Synthesis of `blocking_caveat` Design](#synthesis-of-blocking_caveat-design)
- [🔬 GLS of `blocking_caveat` Design](#gls-of-blocking_caveat-design)
- [❗ Synthesis-Simulation Mismatch (Blocking Caveat)](#synthesis-simulation-mismatch-blocking-caveat)

---

## 🔍 Overview

**What is GLS?**  
Gate-Level Simulation (GLS) is a post-synthesis simulation technique where the synthesized gate-level netlist is simulated to verify its functional correctness against the RTL.

**Why is GLS important?**  
Even though synthesis tools aim to preserve RTL logic, mismatches can occur due to:
- Incomplete sensitivity lists
- Misuse of blocking/non-blocking assignments
- Non-standard Verilog practices

---

## 🔧 Synthesis of Ternary Operator MUX

### 🧪 RTL Simulation

```bash
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

### 🛠 Yosys Synthesis Steps

```bash
# Launch yosys
yosys

# 1. Load Liberty
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# 2. Load RTL design
read_verilog ternary_operator_mux.v

# 3. Run synthesis
synth -top ternary_operator_mux

# 4. Map to technology
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# 5. Visualize
show

# 6. Export netlist
write_verilog -noattr ternary_operator_mux_net.v
```

---

## 🧪 GLS of Ternary Operator MUX

```bash
iverilog ../my_lib/verilog_model/primitives.v \
         ../my_lib/verilog_model/sky130_fd_sc_hd.v \
         ternary_operator_mux_net.v \
         tb_ternary_operator_mux.v

./a.out
gtkwave tb_ternary_operator_mux.vcd
```

✅ Output: GLS matches RTL simulation.

---

## 🚨 Synthesis of Bad MUX Design

**Issue:** `always @(sel)` is incomplete — it ignores `i0`, `i1`, causing latch behavior.

### 🔁 RTL Simulation

```bash
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```

### ⚙️ Yosys Synthesis

```bash
yosys

read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr bad_mux_net.v
```

---

## ⚙️ GLS of Bad MUX Design

```bash
iverilog ../my_lib/verilog_model/primitives.v \
         ../my_lib/verilog_model/sky130_fd_sc_hd.v \
         bad_mux_net.v \
         tb_bad_mux.v

./a.out
gtkwave tb_bad_mux.vcd
```

❌ Output: GLS does not match RTL simulation due to incorrect sensitivity list.

---

## ⚠️ Synthesis-Simulation Mismatch (Bad MUX)

**Cause:**  
RTL simulation only triggers on `sel`, while synthesized hardware triggers on all inputs — creating a logic mismatch.

**Fix:**  
Use:

```verilog
always @(*) begin
    ...
end
```

To ensure the block responds to all input changes.

---

## 📉 Synthesis of `blocking_caveat` Design

**Issue:** Blocking assignments (`=`) inside sequential logic (`always @(posedge clk)`) may cause unexpected results.

### 🧪 RTL Simulation

```bash
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```

### 🛠 Yosys Synthesis

```bash
yosys

read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr blocking_caveat_net.v
```

---

## 🔬 GLS of `blocking_caveat` Design

```bash
iverilog ../my_lib/verilog_model/primitives.v \
         ../my_lib/verilog_model/sky130_fd_sc_hd.v \
         blocking_caveat_net.v \
         tb_blocking_caveat.v

./a.out
gtkwave tb_blocking_caveat.vcd
```

❌ GLS and RTL simulations mismatch due to timing/order differences caused by blocking assignments.

---

## ❗ Synthesis-Simulation Mismatch (Blocking Caveat)

**Cause:**  
Blocking assignments simulate in order, while synthesis may not honor that order exactly in hardware.

**Fix:**  
Use non-blocking assignments (`<=`) for sequential logic.

---

## ✅ Final Tips

| Scenario         | Cause                              | Fix                     |
|------------------|-------------------------------------|--------------------------|
| Bad MUX          | Incomplete sensitivity list         | Use `always @(*)`       |
| Blocking Caveat  | Misuse of `=` in sequential logic   | Use `<=` in `always_ff` |

---

## 🧰 Tools Used

- **Simulation**: `iverilog`, `gtkwave`
- **Synthesis**: `yosys`, `abc`
- **Standard Cells**: `sky130_fd_sc_hd`

---
