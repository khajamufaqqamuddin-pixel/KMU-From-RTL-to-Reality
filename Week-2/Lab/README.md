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



# VSDBabySoC Using Iverilog And Yosys

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
![vsdbabysoc iverilog](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20iverilog.jpeg)
---

🖼️
![vsdbabysoc gtkwave](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20gtkwave.jpeg)
---

🖼️
![vsdbabysoc t_yosys](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20t_yosys.jpeg)
---

🖼️
![vsdbaby yosys](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/Lab/vsdbabysoc%20yosys.jpeg)
---
