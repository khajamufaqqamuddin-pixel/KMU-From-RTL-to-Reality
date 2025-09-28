*****************************************************************************************
# 📘 VSD Hardware Design Program: Combinational & Sequential Logic Optimization

----------------------------------------------------------------------------------------
# 🛠️ Platform: Yosys + Sky130 | 📂 Format: Markdown (for VS Code) | 📄 Author: You
*****************************************************************************************


------------------------------------
🔹 SECTION 1: Combinational Optimization
------------------------------------

## 🎯 Objective
 Optimize logic for area and power by simplifying Boolean expressions and removing unused logic.

## 🔧 Techniques

1. ✅ Constant Propagation
   • Simplifies logic when certain inputs are known constants.
   • Example:
     Y = ((A·B) + C)'  →  If A = 0 ⇒ Y = C'
   • Result: Gate count reduced from 6 transistors to 2.

2. ✅ Boolean Optimization
   • Use Karnaugh Maps (K-Map), Quine-McCluskey.
   • Verilog Example:
     assign y = a ? (b ? c : (c ? a : 0)) : (!c);
     Optimized: y = a ^ c;

## 📦 Yosys Command Snippet

```bash
# Step-by-step for optimization
synth -top <module_name>
opt_clean -purge           # Clean redundant logic
flatten                    # For hierarchical designs
```

* Note:
 * - `opt_clean` removes dead logic.
 * - `flatten` merges all submodules before optimization.
 *


------------------------------------
🔹 SECTION 2: Sequential Optimization
------------------------------------

## 🎯 Objective
Optimize flip-flops, registers, and FSMs to reduce area and improve performance.

## 🔧 Techniques

1. ✅ Sequential Constant Propagation
   • Removes flip-flops whose values are constant.

2. ✅ Advanced Sequential Optimizations
   • FSM State Minimization
   • Retiming (balancing critical paths)
   • Logic Cloning (for congestion/timing fix)



------------------------------------
🔬 SECTION 3: Combinational Optimization Labs
------------------------------------

## 🔍 Lab 1: opt_check.v
Constant propagation example

📷 Diagram:
[Images/1.png], [Images/2.png]

```bash
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v
synth -top opt_check
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

📷 Output:
[Images/5.png]


## 🔍 Lab 2: opt_check2.v
📷 Before → [Images/3.png]
📷 After  → [Images/4.png]

```bash
# Same steps as Lab 1 with different file
```


## 🔍 Lab 5: multiple_module_opt.v
// Hierarchical design - Flatten before optimize

📷 RTL: [Images/13.png], [Images/14.png]

```bash
# Phase 1: Flatten
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module_opt.v
synth -top multiple_module_opt
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
write_verilog -noattr multiple_module_opt_flat.v
```

```bash
# Phase 2: Optimize
yosys
read_verilog multiple_module_opt_flat.v
synth -top multiple_module_opt
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

📷 Output:
[Images/15.png]


------------------------------------
🔬 SECTION 4: Sequential Optimization Labs
------------------------------------

## 🔍 Lab 1: dff_const1.v
Reset doesn't immediately affect output
FF is preserved

📷 Design: [Images/20_a.png]
📷 Waveform: [Images/20_wave.png]
📷 Result: [Images/20.png]

```bash
yosys
read_verilog dff_const1.v
synth -top dff_const1
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

## 🔍 Lab 2: dff_const2.v
Output is constant → FF removed

📷 Waveform: [Images/21_wave.png]
📷 Output: [Images/21.png]


## 🔍 Lab 6: counter_opt.v
Only count[0] is used → Tool optimizes out count[1:2]

📷 Before opt_clean:
[Images/counter_5.png], [Images/counter_1.png]

📷 After opt_clean:
[Images/counter_2.png]

```bash
opt_clean -purge
```


------------------------------------
📘 FINAL NOTES
------------------------------------

## ✅ Best Practices Summary

- Always `flatten` hierarchical designs before running optimizations.
- Use `opt_clean -purge` after synthesis to eliminate dead logic.
- Use `abc` for mapping to the standard cell library.
- Verify optimizations visually using the `show` command.

## 📚 Tools & References

- 🔧 Yosys: https://yosyshq.net/yosys/
- 📁 Liberty File: `sky130_fd_sc_hd__tt_025C_1v80.lib`
- 🧠 Sky130 PDK: https://github.com/google/skywater-pdk


