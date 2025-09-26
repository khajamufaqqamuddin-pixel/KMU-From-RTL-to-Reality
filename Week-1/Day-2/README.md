# ⚙️ VSD Hardware Design Program

## ⏱️ Timing Libraries, Synthesis Techniques & Flip-Flop Styles

### 📂 Table of Contents
- 🔹 [Liberty Format Overview](#liberty-format-overview)
- 🔹 [Standard Cell Case Study: `a2111o_1`](#standard-cell-case-study-a2111o_1)
- 🔹 [AND Cell Comparison: `and2_1`, `and2_2`, `and2_4`](#and-cell-comparison-and2_1-and2_2-and2_4)
- 🔹 [Synthesis Approaches: Hierarchical vs Flat](#synthesis-approaches-hierarchical-vs-flat)
- 🔹 [Why Flip-Flops? Understanding Glitch Prevention](#why-flip-flops-understanding-glitch-prevention)
- 🔹 [Flip-Flop Types & RTL Design](#flip-flop-types--rtl-design)
- 🔹 [RTL-to-Gate-Level Synthesis with Yosys](#rtl-to-gate-level-synthesis-with-yosys)
- 🔹 [Smart Optimizations & Minimal Logic](#smart-optimizations--minimal-logic)

---

## 📘 Liberty Format Overview

The **Liberty format (`.lib`)** defines cell timing, power, area, and functionality in standard cell libraries. It is split into:

- 📌 *Global Parameters*: units, technology, operating corners.
- 📌 *Cell-Specific Details*: logic function, pins, timing arcs, power.

Lib files exist for different corners: `tt`, `ss`, `ff` (typical, slow, fast).

---

## 🧱 Standard Cell Case Study: `a2111o_1`

This cell implements:





➡️ Found in `sky130_fd_sc_hd__tt_025C_1v80.lib`.

---

## 🧮 AND Cell Comparison: `and2_1`, `and2_2`, `and2_4`

These are different **drive-strength versions** of a 2-input AND gate:
| Cell Name | Drive Strength | Use Case |
|-----------|----------------|----------|
| `and2_1`  | 1x             | Low-load |
| `and2_2`  | 2x             | Medium-load |
| `and2_4`  | 4x             | High-load |

---

## 🏗️ Synthesis Approaches: Hierarchical vs Flat

### 🔸 Hierarchical
- Maintains submodules.
- Ideal for **large designs**.
- Better **tool memory optimization**.

### 🔸 Flat
- Collapses all modules into a single top-level.
- Suitable for **small designs**.
- Easier **gate-level analysis**.

> Use `flatten` in Yosys to convert to flat structure.

---

## ⚠️ Why Flip-Flops? Understanding Glitch Prevention

Combinational logic can glitch due to race conditions.  
✅ Flip-flops sample data **only on clock edges**, filtering out intermediate glitches.

⏱️ Flip-flops enable **stable pipeline behavior**.

---

## ⏹️ Flip-Flop Types & RTL Design

| Type                             | Behavior Summary                           |
|----------------------------------|--------------------------------------------|
| Async Reset (`dff_asyncres`)     | `q = 0` immediately if reset high          |
| Async Set (`dff_async_set`)      | `q = 1` immediately if set high            |
| Sync Reset (`dff_syncres`)       | `q = 0` at clock edge if reset high        |
| Async + Sync Reset               | Async reset overrides sync reset           |

> Always blocks vary by sensitivity: `posedge clk`, `posedge rst`, etc.

---

## 🛠️ RTL-to-Gate-Level Synthesis with Yosys

```bash
# Start yosys
yosys

# Load tech library
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# Read RTL
read_verilog <module>.v

# Run synthesis
synth -top <module>

# Optional: Map to standard DFF cells
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# Technology mapping
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

# View synthesized schematic
show
