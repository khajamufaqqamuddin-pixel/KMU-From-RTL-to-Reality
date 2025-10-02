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
