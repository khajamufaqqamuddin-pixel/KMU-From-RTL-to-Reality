## 🧠 VSD  – Week 1  RISC-V SoC Tapeout Program – My Design Journey

<div align="center">


</div>



## 🧭 About This Repository

This repository documents my week-by-week experience participating in the **VSD - RISC-V SoC Tapeout Program** — India’s largest open-source silicon tapeout initiative. We start with RTL design fundamentals and go all the way to GDSII generation using open-source EDA tools and the Sky130 PDK.

💡 This is **not just theory** — we build actual, synthesizable hardware and validate it using industry-grade flows.

---

## 🛠️ Tools & Tech Stack

- **RTL Simulation**: Icarus Verilog (iverilog)
- **Waveform Analysis**: GTKWave
- **Synthesis & Tech Mapping**: Yosys + Sky130 Standard Cell Library
- **GLS Simulation**: Icarus Verilog with synthesized netlist
- **Visualization**: `show` in Yosys
- **Target Tech**: SkyWater Sky130 PDK

---

## 📅 Weekly Progress Overview

| Week | Topics Covered                            | Status     |
|------|--------------------------------------------|------------|
| 0    | Tool Setup – Icarus, Yosys, GTKWave        | ✅ Complete |
| 1    | RTL → GLS Flow, Multiplexers, Adders       | ✅ Complete |
| 2    | TBD                                         | 🔜 Upcoming |

---

## 📘 Week 0 – Environment Setup

**Goal:** Prepare Linux environment for RTL simulation and synthesis.

### ✅ Tools Installed:
- Icarus Verilog (RTL Simulation)
- GTKWave (Waveform Viewer)
- Yosys (Synthesis)

### 🔑 Key Outcomes:
- All tools verified with sample designs.
- Ready for RTL → GDSII design flow.

---

## 🔧 Week 1 – RTL Design, Synthesis & GLS

**Main Focus:** RTL to gate-level netlist generation + verification using Yosys and iverilog.

### ✅ Tasks Completed:

| Task | Description                                                |
|------|------------------------------------------------------------|
| 1    | MUX synthesis with `opt_clean -purge`                      |
| 2    | DFF constant mapping (with reset logic)                    |
| 3    | MUX using `for-generate` + GLS comparison                  |
| 4    | DEMUX using `generate` block                               |
| 5    | Ripple Carry Adder design and gate-level simulation        |

### 🔍 Highlights:

- Understood **synthesis optimizations** like dead logic removal.
- Debugged **latch inference issues** in GLS and fixed using Sky130 primitives.
- Verified **GLS vs RTL waveform equivalence** across designs.
- Applied knowledge to **custom filter design** for further exploration.

---

## 📊 Visualization Snapshots

> Replace these with your actual images/screenshots in your repo:

- ✅ `mux_generate_GLS.v` netlist  
  ![MUX Netlist](Images/mux_generate_show.png)

- 🧪 `tb_rca.v` simulation waveform (GLS vs RTL)  
  ![RCA Simulation](Images/Task5_rca_GLS_and_RTLsimulaltion.png)

- 🔄 `const4.v` constant propagation  
  ![Const4](Images/Task2_dff_const4_show_iverilog_simuatlion.png)

---

## 💡 Key Technical Learnings

- 🧠 Difference between **behavioral and structural Verilog**.
- 🧹 Usage of `opt_clean -purge` to eliminate dead logic.
- ⚠️ How **incomplete `if` or `case`** blocks result in latch inference.
- 🔁 Role of **blocking vs non-blocking assignments**.
- 📈 Importance of **Gate-Level Simulation** for synthesis validation.

---

##  Acknowledgments

A huge thank you to:

- [Kunal Ghosh](https://github.com/kunalg123) – Founder, VSD
- [VSD Team](https://vsdiat.vlsisystemdesign.com/)
- [RISC-V International](https://riscv.org/)
- [India Semiconductor Mission (ISM)](https://ism.gov.in/)
- [Efabless](https://efabless.com/) – Open-source tapeout platform

---

## 🔗 Useful Links

[🔹 VSD Program Site](https://vsdiat.vlsisystemdesign.com/)  
[🔹 RISC-V International](https://riscv.org/)  
[🔹 Sky130 PDK on GitHub](https://github.com/google/skywater-pdk)  
[🔹 Efabless Platform](https://efabless.com/)

---





