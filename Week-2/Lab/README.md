# Week-2  Lab
---
# File Path
Clone The Git And Follow The File Path
```bash
$ git clone https://github.com/manili/VSDBabySoC.git
$ ls
$ cd VSDBabySoC
$ ls
$ cd src
$ cd module
$ ls
```

🖼️
![file path](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/file%20path.jpeg)



---



# BabySoC Using Iverilog And Yosys

---


```bash
$ ls
$ cd VSDBabySoC
$ ls
$ cd src
$ cd module
$ ls
$ iverilog vsdbabysoc.v rvmyth.v avsddac.v avsdpll.v testbench.v
$ ./a.out
$ gtkwave dump.vcd
$ yosys
> read_liberty -nooverwrite -lib /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> read_verilog avsdpll_stub.v
> read_verilog avsddac_stub.v
> read_verilog rvmyth.v
> read_verilog vsdbabysoc.v
> synth -top vsdbabysoc
> abc -liberty /home/kmu/Desktop/yosys/sky130RTLDesignAndSynthesisWorkshop/verilog_files/open_pdks/sources/sky130_fd_sc_hd/timing/sky130_fd_sc_hd__tt_025C_1v80.lib
> show vsdbabysoc
```

---
🖼️
![gvim](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/gvim.jpeg)
---



🖼️
![gvim_tb](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/gvim_tb.jpeg)
---

🖼️
![babySoC iverilog](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/%20babySoC%20iverilog.jpeg)
---

🖼️
![babySoC gtkwave](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/babySoC%20gtkwave.jpeg)
---





# 🔍 Observations from GTKWave Simulation (`dump.vcd`)

## ✅ Overview
The simulation was executed using the testbench `vsdbabysoc_tb` and analyzed in **GTKWave** over a duration of **85 µs**. The waveform data provides insights into the behavior of a simple SoC or PLL-based design. Below is a summary of the key signals observed.

---

## 📈 Signal Observations

### 1. `reset` (reg)
- Remained **low (0)** throughout the simulation.
- Indicates that no reset was applied during this time window.
- All modules were active from the beginning of the simulation.

### 2. `ENb_CP` and `ENb_VCO` (reg)
- Both are active-low enable signals (`ENb_` implies active-low).
- Remained **low**, which means both **charge pump** and **VCO** blocks were **enabled**.

### 3. `REF` (reg)
- A periodic digital signal (square wave).
- Functions as the **reference input** clock, likely for a PLL.

### 4. `VCO_IN` (reg)
- Another periodic digital signal, similar to `REF`.
- Frequency closely matches that of `REF`, suggesting that the **PLL is locked** or tracking the reference.

### 5. `OUT` (real)
- A real-valued analog signal, possibly representing the output of the charge pump or filtered VCO signal.
- Shows expected continuous variation, reflecting dynamic analog behavior.

### 6. `VREFH` and `VREFL` (real)
- Constant reference voltages:
  - `VREFH ≈ 3.3V`
  - `VREFL ≈ 0V`
- These likely serve as high/low reference levels for analog comparison.

---

## 📌 Summary

- All modules remained active since the reset signal was never asserted.
- The system appears to be stable and functional.
- The PLL subsystem seems to be **locked**, as `REF` and `VCO_IN` are synchronized.
- Analog output (`OUT`) is behaving as expected.
- Reference voltages (`VREFH`, `VREFL`) are within normal operating range.

---



🖼️
![pll](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/pll.jpeg)
---




🖼️
![vsdbabysoc t_yosys](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20t_yosys.jpeg)
---

🖼️
![vsdbaby yosys](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20yosys.jpeg)
---
